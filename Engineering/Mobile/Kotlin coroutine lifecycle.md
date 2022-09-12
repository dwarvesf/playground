---
tags: mobile, kotlin
author: Truong Hung Khanh
date: 2022-09-08
---

As you may know about coroutine previouslyc, coroutine is a structured concurrency, which means it can control flow to ensure that every concurrent tasks work well until it completed or being canceled. Because of that, each coroutine have it own lifecycle and scope, represent by CoroutineContext and CoroutineScope.

## Difference between Coroutine context and Coroutine scope

Before we deep dive 

Reference from [Kotlin - doc](https://kotlinlang.org/docs/coroutines-and-channels.html#structured-concurrency)
> `Coroutine scope` is responsible for the structure and parent-child relationships between different coroutines. New coroutines usually need to be started inside a scope.
- FYI: coroutine builder like `launch` or `async` all inherits CoroutineScope. Which means you cannot run a coroutine without CoroutineScope.

>`Coroutine context` stores additional technical information used to run a given coroutine, like the coroutine custom name, or the dispatcher specifying the threads the coroutine should be scheduled on.
- It is also responsible for the coroutine’s lifecycle, cancellation, and parent-child relations.

## Cancellation and timeout

## Conclusion