---
tags: Mobile, Kotlin
author: Truong Hung Khanh
date: 2022-09-06
---

Start from Kotlin 1.3, JetBrain introduce coroutine a light-weight threads. This article will focus on basic concept of coroutine and how you can use it in Kotlin.

## Coroutine overview

Coroutine, an instance of suspendable computation that takes a block of code and run it on concurrently with the rest of the program. Concept of coroutine is familar with thread but coroutine does not bound to any particular thread. It can suspend its execution in this thread and resume it on another one.

## Structured concurrency

Before we dive into how we can use Coroutine in Kotlin, let me first introduce Structured concurrency, the principle of coroutine.

>Due to [wikipedia](https://en.wikipedia.org/wiki/Structured_concurrency), the core concept is to encapsulate the concurrent threads of execution, so that we can control the flow construct with clear entry and exit points. Also, ensure all children must be completed before exit. A scenario that proves this pattern:

Let's say you want to make breakfast with fried eggs and bread. I assume that we have a total of 3 tasks that need to be done:
- Frying the eggs
- Put our bread into the toaster
- Bring everything on a disk

Structured concurrency present that all sub-tasks shall complete before the completion of their parent task(s). No sub-tasks can outlive its parent task(s). The principle also ensures that any errors that happen in its child are properly reported and are never leaked.

## Kotlin coroutines

You can run the following code block on [Kotlin playground](https://play.kotlinlang.org/).

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    // Parent task
    val parentJob = launch {

        // Child task
		launch {
            var count = 1
            while (count <= 5) {
                println("Count: $count")
                delay(100)
                count++
            }
        }
    }

    delay(250)
    println("Cancelling parent job")
    parentJob.cancel()
}

--------------- Output ----------------
Count: 1
Count: 2
Count: 3
Cancelling parent job
```

Let's me explain some basic functions:
- `runBlocking {...}` is a coroutine builder. It is designed to bridge the non-coroutine code of a regular `fun main()` with all coroutine code inside `runBlocking` lambda.
- `launch {...}` is also a coroutine builder. Use this when you want to launch a new coroutine concurrently with the rest of the code, that can continues to work independently.
- `delay()` is a suspend function, this work almost the same as `sleep()` function from Java. But because this is a suspend function, it does not block the current thread and allows other coroutines code to run and use the current thread.

As we know [[structured concurrency]] principle, all sub-tasks cannot outlive their parent task. The example above shows exactly this when the child's task can only print count 3 times before its parent canceled. 

But if we have a very important task that has to be completed even if its parent is going to cancel, can we do that? The answer is yes, but we have to understand why child tasks is canceled in the first place.

## Cancellation

Not always the code inside the coroutine is canceled when its parent finish. We have two bullet points that need to be clear:
- First, we are the one who chooses to continue to execute the child's task or not, even when the parent's task has been canceled
- Second, a child's task that runs after its parent cancels is not prove our principle wrong. Because the parent task does not actually close, it will wait until it child tasks finish before the cancellation can start.

The reason behide the cancellation is the [Job state](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/-job/). Each job has a lifecycle of its own, and the final state it can achieve is `completion`.

Below is a state machine diagram that shows every state a coroutine could have in its life time.

```
                                          wait children
    +-----+ start  +--------+ complete   +-------------+  finish  +-----------+
    | New | -----> | Active | ---------> | Completing  | -------> | Completed |
    +-----+        +--------+            +-------------+          +-----------+
                     |  cancel / fail       |
                     |     +----------------+
                     |     |
                     V     V
                 +------------+                           finish  +-----------+
                 | Cancelling | --------------------------------> | Cancelled |
                 +------------+                                   +-----------+
```
> Ref: Job states - [Kotlin document](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/-job/)

As you can see in the diagram, when the state is `Active` and want to transition to `Completed` it has to wait for children to complete their work before finishing. It's weire right, you may ask why example above work different with this diagram, but the truth is that parent would wait its children state all changes to `completed` before it can `completed`. The example is using one special suspend function in the code that is the `delay()` function.

Delay function is a `suspendCancellableCoroutine`. This means during the delay, if the parent task cancellation happens, this child task also cancels itself at the same time. So the next time you want to use the build-in suspend function, make sure you read it carefully.

To prove what I jsut said, consider run the following code:
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    val parentJob = launch {
        val childJob = launch {
            var count = 1
            val startTime = System.currentTimeMillis()
            var nextPrintTime = startTime
            while (count <= 5) {
                if (System.currentTimeMillis() >= nextPrintTime) {
                    println("Count: $count")
                    nextPrintTime += 100L
                    count++
                }
            }
        }
    }

    delay(250)
    println("Cancelling parent job")
    parentJob.cancel()

    println("Parent job completed")
}

--------------- Output ----------------
Count: 1
Count: 2
Count: 3
Count: 4
Count: 5
Cancelling parent job
Parent job completed
```

## Light-weight thread

The final thing to keep in mind, coroutines are light-weight threads which means they will use fewer resources than the JVM threads. One way to check this behavior is that spamming threads and coroutines at the same time and checking with one uses more memory than the other. I have copy paste a block code from the Kotlin doc below, you can try to run it on the playground and see what happens lul.

Try to launch 1000 coroutines:
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    repeat(1000) { // launch a lot of coroutines
        launch {
            delay(5000L)
            print(".")
        }
    }
}
```

Try to launch 1000 threads:
```kotlin
import kotlin.concurrent.thread

fun main() {
    repeat(1000) {
        thread {
            Thread.sleep(5000L)
            print(".")
        }
    }
}
```

## References

[Article - Structured concurrency](https://proandroiddev.com/structured-concurrency-in-action-97c749a8f755#:~:text=%E2%80%9CStructured%20concurrency%E2%80%9D%20refers%20to%20a,scope%20of%20a%20parent%20operation.)
[Kotlin doc - Coroutine basic](https://kotlinlang.org/docs/coroutines-basics.html)
