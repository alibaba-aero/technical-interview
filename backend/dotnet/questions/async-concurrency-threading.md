# Async/Concurrency/Threading

* Concurrency vs Multi-Threading vs Async vs Parallelism
* Data-Structures
	* ConcurrentDictionary
	* ConcurrenctQueue
	* Channels
* Async & Task Internals
	* At least, how many threads are needed to run an async task?
	* GetAwaiter().GetResult() vs .Result
	* Task vs ValueTask
	* Task.WhenAll & Task.WhenAny
	* Why is `async void` bad? When do we have to use it?
	* Task.Run
		* What does it do?
		* Does Task.Run() create a new Thread?!
		* Exception-Handling in Fire & Forget scenarios
	* Thread.Sleep vs Task.Delay
	* CancellationToken
		* Usages
		* Creating a cancellation-token using CancellationTokenSource
		* Canceling a CPU-Bound Task
		* How can we timeout an async task after some time using CancellationTokens?
	* IAsyncStateMachine
		* What's that?
		* How does it work internally?
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
