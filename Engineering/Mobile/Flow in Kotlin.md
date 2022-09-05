---
tags: mobile, android, kotlin, flow
author: Truong Hung Khanh
date: 2022-09-05
---

## **What is a Flow in Kotlin?**

- It’s a Kotlin language feature that serves as a reactive programming framework
- It’s all about being notified about changes in your code and sending them through a pipeline that potentially modifies them
- A Flow is a coroutine that can emit multiple values over a period of time

## **Count-down example**

First, let's see an example of how can we declare a flow. Remember it, we are going to use this example a few times below.

```kotlin
class MainViewModel: ViewModel() {

	// Create an integer flow
	val countDownFlow = flow<Int> {
		val startingValue = 10
		val currentValue = startingValue

		while(currentValue > 0) {
			// Because we are currently on a coroutine, we can call delay here
			delay(1000L)
			currentValue--

			// We emit the new value for the countDownFlow variable
			// This value will notify all subscribers that subscribe to our flow
			emit(currentValue)
		}
	}
}
```

![Countdown.png](https://khanhth-public-image-raw.s3.ap-southeast-1.amazonaws.com/work/brainery-assets/Countdown+(1).png)

The above image shows how flow emits data every second. But when and where those data will arrive to?

### Collecting the results

On the downstream of flow, we have plenty of ways to collect results, like `collect`, or `collectLatest` operations

- `Collect` operator will let you know whenever new data is emitted in the flow. Collect can also start a cold flow(I will explain more in a later session)
- `CollectLatest` in the order hand, only alert you the last data the source emitted.

**Diff between Collect and CollectLatest**

You may wonder what is the different between `Collect` and `CollectLatest`. 
- The behavior of `Collect` is that while the collector is doing his work, all emitting work will be pending. 
![PendingWhileCollect.png](https://khanhth-public-image-raw.s3.ap-southeast-1.amazonaws.com/work/brainery-assets/CountDownCollectPendin+(1).png)
- But `CollectLatest` forcing the collector to start over.
![CollectLatest](https://khanhth-public-image-raw.s3.ap-southeast-1.amazonaws.com/work/brainery-assets/CoutnDownCollectLatest+(1).png)

So using `CollectLatest` on UI observation will be the better choice to reflect the state.
        
### Flow operations

In real life, we can see a lot of different cases/problems, and not many of them can resolve in the same way. So let me introduce you to some of the operators that can help to organize data.

- **Intermediate operations** are the operations that won't invoke the stream, instead its functionality will modify the stream. We have some operations like:
    - `Filter` operator, allow you to filter out what you don’t need downstream by returning bool value to the filter lambda.
    - `Map` in flow is different from the map in RX. When map in RX can only transform the `data type`, map in flow can both transform `data value`, and `data type`
    - `onEach` operator is going to notify you whenever an item is emitted from a flow, but it won’t start the cold flow like collect should be
    - `Catch` collect operator won’t receive any call whenever an error happens. Instead catch will be notified with an exception.
    - `Buffer` is working like a `queue` when `flow` emits quicker than the `collector` can consume, we will buffer it under the queue and execute it in `FIFO` order. The `configuration` allows us to control `capacity` and if the `boundary limit` reaches, we can drop or suspend the queue.
    - `Conflate` similar to buffer but the collector will only get the latest data available, and skipped the rest if the collector cannot finish his work at the time.
    - `Collect Latest` is the harshest. It works similarly with `conflate`, except it won't wait for a `collector` to finish his job. Instead, it force the collector to start the job from the beginning.
- **Terminal operations**, this kind of operation will invoke the flow.
    - `Count` return a number of item that match the term
    - `Reduce` whenever a new data emitted, we can access to the `Accumulator` variable of previous calculation.
    - `Fold` is work the same as `Reduce` but support initial value
    - `FlatMap`
        - `flatMapConcat`, a basic flatten function. Use this when you want to flattening a `flow` in a `flow`
        - `flatMapMerge` execute all the flows at the same time.
        - `flatMapLatest` is like `collectLatest`, it only wait for the last item emitted

### Cold Flow vs Hot Flow

- `Cold flow` means that this flow won’t gonna do its job until one collector starts to observe it.
    - `Flow` itself is the cold flow
    ![ColdFlow](https://khanhth-public-image-raw.s3.ap-southeast-1.amazonaws.com/work/brainery-assets/ColdFlow+(1).png)
- `Hot flow` On the other hand, hot flow stands for a flow that doesn’t care about the `collector`, after it `initializes`, it will start its own job and emit data for the collector when they start to `observe` or after the `emission`
    - `StateFlow` is one of the basic hot flow
    ![HotFlow](https://khanhth-public-image-raw.s3.ap-southeast-1.amazonaws.com/work/brainery-assets/HotFlow+(1).png)

### StateFlow

As we know StateFlow is hot, but what is a state flow?

> [StateFlow](https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-state-flow/) is a state-holder observable flow that emits the current and new state updates to its collectors. The current state value can also be read through its [value](https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-state-flow/value.html)
 property. To update state and send it to the flow, assign a new value to the `value`
 property of the [MutableStateFlow](https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-mutable-state-flow/index.html) class.

*Reference : [State flow - Google documentation](https://developer.android.com/kotlin/flow/stateflow-and-sharedflow#stateflow)*
> 

An observable means we can observe it and do some UI mapping right? Yes, and if you know `LiveData`, both follow a similar pattern.

```kotlin
// MainActivity.kt
override fun onCreate(savedInstanceState: Bundle?) {
	// Start a coroutine in the lifecycle scope
	lifecycleScope.launch {
		repeatOnLifecycle(Lifecycle.State.STARTED) {
			viewModel.newsUiState.collect { newsUiState ->
				// New value received
				when (newsUiState) {
					is newsUiState.Success -> showFavoriteNews(uiState.news)
					is newsUiState.Error -> showError(uiState.exception)
				}
			}
		}
	}
}
```

**Notes**
- ⚠️ If you use `launch` or `launchIn` operator and want to update the UI, you can archive some `ANR`(App Not Response). This is because collectors of a StateFlow can be notified after the UI is already destroyed.
- 💡 So collecting flow under `repeatOnLifecycle(Lifecycle.State.STARTED)` lambda will ensure your flow starts listening for values on lifecycle `STARTED` state and stops when lifecycle is at `STOPPED` state

### Context

Usually, when you work with asynchronous, you must be aware of the thread you are currently running on like `Main Thread`, `Computation Thread`, or `IO Thread`. In Flow, the thread you are going to use is the thread you call the `collect` operator.

**For example:**
The snippet code below shows how can you observe a flow on the Main thread.
```kotlin
// MainActivity.kt
override fun onCreate(savedInstanceState: Bundle?) {
	// This will be executed on Dispatches.Main(Main Thread)
	lifecycleScope.launch {
		viewModel.userFlow.collect { user ->	
			// ...
		}
	}
}
```

But this will not be applicable if you have work that requires CPU-consuming computation or network calls. For this kind of problem, `Flow` expects you to use some operators to switch the context like:
- `withContext` Allow you to switch the context(thread) of the flow
    **For example:**
    Wrapping your flow code block inside `withContext` lambda will allow it to switch from the current context to other like IO thread
    ```kotlin
    // In ViewModel.kt
    val postFlow = flow {
    	// Code block inside withContext will be executed
    	// on Dispatchers.IO which is the IO thread
    	withContext(Dispatchers.IO) {
    		// ...
    	}
    
    	// Outside withContext will run on the collector thread
    }
    
    // Later in MainActivity.kt
    fun fetchPosts() {
    	lifecycleScope.launch {
    		viewModel.postFlow.collect {
    			// ...
    		}
    	}
    }
    ```
    **Notes:** This approach has a limitation, that you will end up with a lot of boilerplate code.
- `flowOn` is an operator that allows us to change the context of this flow but it's only applied to the flow before `flowOn` operator.
    - The below example will clarify what I mean. `postFlow` itself will always run on the Background thread, but emit data to a collector on the Main thread where it being collected.
    ```kotlin
    val postFlow = flow {
    	// postFlow will run on IO thread
    }.flowOn(Dispatchers.IO)
    
    // Later in MainActivity.kt
    fun fetchPosts() {
    	// Collecting are being called on Main Thread
    	lifecycleScope.launch {
    		viewModel.postFlow.collect {
    			// ...
    		}
    	}
    }
    ```
    - You can also apply many `flowOn` operators, to perform different jobs in different contexts.
    ```kotlin
    val userFlow = flow {
    	// network call on IO thread
    }.flowOn(Dispatchers.IO)
    .map { user ->
    	// Execute avatar mapping on the Background thread
    	user.avatar = "https://imageurl.com/${user.avatar}"
    	user
    }.flowOn(Dispatchers.Default)
    
    // Later in MainActivity.kt
    fun fetchPosts() {
    	lifecycleScope.launch {
    		viewModel.userFlow.collect { user ->
    			// Update UI on the Main thread
    			updateUI(user)
    		}
    	}
    }
    ```
    

### Lifecycle-aware

The final thing you want to keep in mind when executing an asynchronous work is that you have to be flexible to cancel it. For example, a network call can crash your app if its parent is killed.
- The reason is that flow tries to access the instance that the system has already invalidated.

For the above problem, Flow in Android supports lifecycle-aware. You can launch flow in the exact scope you need, and Flow will be canceled whenever the scope is invalid.
- `viewModelScope` Any coroutine launched in this scope is automatically canceled if the `ViewModel` is cleared. Coroutines are useful here for when you have work that needs to be done only if the `ViewModel` is active. 
    - For example, if you are computing some data for a layout, you should scope the work to the `ViewModel` so that if the `ViewModel` is cleared, the work is canceled automatically to avoid wasting resources.
    ```kotlin
    class MyViewModel: ViewModel() {
        init {
            viewModelScope.launch {
                // Will be clear right after viewModel invalidated
                postFlow.collect {
                    // ...
                }
            }
        }
    }
    ```
    
- `lifecycleScope` is defined for each [Lifecycle](https://developer.android.com/topic/libraries/architecture/lifecycle) object. Any coroutine launched in this scope is canceled when the Lifecycle is destroyed. But remember to wrap the code with `repeatOnLifecycle(Lifecycle.State.STARTED)` if you are programming on Android.
    
    ```kotlin
    class MyFragment: Fragment() {
        override fun onViewCreated(view: View, savedInstanceState: Bundle?) {
            super.onViewCreated(view, savedInstanceState)
            viewLifecycleOwner.lifecycleScope.launch {
                repeatOnLifecycle(Lifecycle.State.STARTED) {
                    // observing flow
                }
            }
        }
    }
    ```
    

## More advance keywords

- CallbackFlow, allow you to send data to a different coroutine:
[https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/callback-flow.html](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/callback-flow.html)
- StateFlow is a SharedFlow:
[https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-shared-flow/](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-shared-flow/)
- Channel, with this we can communicate between flows:
[https://kotlinlang.org/docs/channels.html](https://kotlinlang.org/docs/channels.html)
- Even more operators: 
[https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/)
- Flow testing:
[https://developer.android.com/kotlin/flow/test](https://developer.android.com/kotlin/flow/test)

## References

- [https://developer.android.com/kotlin/flow](https://developer.android.com/kotlin/flow)
- [https://developer.android.com/topic/libraries/architecture/coroutines#suspend](https://developer.android.com/topic/libraries/architecture/coroutines#suspend)
- [https://elizarov.medium.com/execution-context-of-kotlin-flows-b8c151c9309b](https://elizarov.medium.com/execution-context-of-kotlin-flows-b8c151c9309b)
- Series: [https://www.youtube.com/watch?v=ZX8VsqNO_Ss&list=PLQkwcJG4YTCQHCppNAQmLsj_jW38rU9sC](https://www.youtube.com/watch?v=ZX8VsqNO_Ss&list=PLQkwcJG4YTCQHCppNAQmLsj_jW38rU9sC)