# Async/Concurrency/Threading

* Concurrency vs Multi-Threading vs Async vs Parallelism
* Data-Structures
	* ConcurrentDictionary
	* ConcurrenctQueue
	* Channels
* Async & Task Internals
	* How many threads at least needed to run an async task?
	* GetAwaiter().GetResult() vs .Result
	* Task vs ValueTask
	* Task.WhenAll & Task.WhenAny
	* Why `async void` is bad? When we have to use them?
	* Task.Run
		* What does it do?
		* Does Task.Run() creates a new Thread?!
		* Exception-Handling in Fire & Forget scenarios
	* Thread.Sleep vs Task.Delay
	* CancellationToken
		* Usages
		* Creating a cancellation-token using CancellationTokenSource
		* Canceling a CPU-Bound Task
		* How can we timeout an async task after some time using CancellationTokens?
	* IAsyncStateMachine
		* What's that?
		* How it works internally?
	* IAsyncEnumerable
	* IAsyncDisposable
		* What's that?
		* Where do we need that?
* Locking
	* Ways
		* `lock` keyword
		* Monitor.Enter
		* Semaphore
		* Semaphore-Slim
	* Strategies
		* Optimistic
		* Pessimistic
* ThreadPool
	* What's thread-pool?
	* Why should we use that?
	* How can we run a piece of code on a thread-pool thread? (ThreadPool.QueueUserWorkItem)
