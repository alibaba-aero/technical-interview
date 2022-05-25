# Concurrency

* Concurrency
 * What is concurrency?
 * How is it different from parallelism?
* Race conditions
 * What is a race condition?
 * Why is it important?
 * What are different types of race conditions?
 * When do race conditions occur?
 * How we can prevent it?
* Synchronization
 * What is memory synchronization?
 * What problem does it solve?
 * How we can achieve it?
 * What benefits and drawbacks does it provide?
 * When we should use it?
* Deadlocks, Livelocks, Starvation
 * What is it?
 * When does it occurs?
 * How we can prevent it?
 * What is dining philosophers' problem?
* Transactions
 * What is a transaction?
 * What problem does it solves?
 * How does it affects the application?
 * What is atomicity and how we can achieve it?
 * What is isolation and how we can achieve it?
 * What are different isolation levels?
* Goroutine
 * Definition
 * What is goroutine?
 * How is it different with Thread/Process/Coroutine/Green Thread?
 * Goroutine Leak
 * What is a goroutine leak and how we can prevent it?
 * Why is it important?
 * Race Detection
 * How we can detect it before runtime?
 * Is there any way to detect race conditions on runtime?
 * How reliable is it?
 * Do you know how Goroutine scheduler works?
* Channels
 * What is a channel and why do we use it?
 * There is a proverb ["Don't communicate by sharing memory, share memory by communicating"](http://go-proverbs.github.io). What does it mean?
 * What is the difference between buffered and unoffered channels? and when we use either of them?
 * How do read-only/write-only channels help us?
* sync package
 * What is the use case of sync packages and types?
 * What is the use case of each type in this package?
* Patterns
 * Async
 * We don't have async keywords in golang like some other languages. How can we achieve the same behavior in Go?
 * Why and where do we need to use this pattern?
 * Queue
 * How can we create a queue in golang?
 * How can we add rate limiting and policy to the queue?
 * Does changing sync and sequential process into an async one with queue really help scalability? Why?
 * How do queues change application behavior?
 * Why and where do we need to use this pattern?
 * Pipelines
 * What is a pipeline?
 * What are the different ways to implement it?
 * Why and where do we need to use this pattern?
 * Fan-In and Fan-Out
 * What is Fan-In/Fan-Out?
 * How we can implement it?
 * Why and where do we need to use this pattern?
 * Heartbeats
 * What are Heartbeats?
 * How we can implement it?
 * How it can help us? What benefits and drawbacks does it have?
 * Why and where do we need to use this pattern?
 * Timeouts and Cancellation
 * Can you describe a scenario where you need to cancel/timeout a Goroutine?
 * How we can handle timeouts and cancellations of Goroutines?
 * How it can affect application behavior? What do we need to consider?
 * Error propagation
 * How we should propagate errors between Goroutines?
 * What happens when we want structured errors?
 * Work stealing
 * What is work stealing?
 * How can we implement it?
 * How can it help us?
 * Where should we use this?
