Concepts  similar to Kotlin Coroutines

Concurrency - Multiple task can be done concurently.<br>
Parallelism - Executes multiple tasks simultaneously.

Thread

    - Have their own execution stack.
    - Fixed stack space (~1MB).
    - Managed by OS.

goroutines

    - Have their own execuion stack.
    - Varibale stack space (starts @2kb).
    - Managed by Go runtime.

Challenges with concurrency

    - Coordinating tasks. (waitgroups, channels)
    - Shared memory. (mutexes, channels)

WaitGroups

    - A wait group waits for a colllection of goroutines to finish.

Mutex

    - A mutually exclusive lock.
    go run --race .

Channels

    - Dont communicate by sharing memory, share memory by communicating. - Rob Pike.
    - Channel supports coordinating task and shared memory.
    - ch := make(chan int) // creating a channel.
    - ch := make(chan int, 5) // creating a buffered channel.

Channel Type

    - Bidirectional (default)
    - send-only
    - receive-only
    ch := make(chan int) // bidirectional
    func(ch chan int){...} // bidirectional
    func(ch chan<- int){...} // send-only channel
    func(ch <-chan int>){...} //receive-only channel
    - cannot check for closed channel.
    - sending new message triggers a panic.
    - Receiving message is ok
    - If buffered, all messages available.
    - If unbuffered, or empty, receive zero-value.
    - channel can be closed only on send-only/bidirectional channels not on receive-only channel.
    - Blocking select statement. When a goroutine is blocked when all cases of the select statement is blocked.
    - default case used for non-blocking select.
