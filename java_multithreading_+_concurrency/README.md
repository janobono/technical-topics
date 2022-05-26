# Java Multithreading + Concurrency

Java Concurrency is a term that covers multithreading, concurrency and parallelism on the Java platform. That includes
the Java concurrency tools, problems and solutions.
Multithreading means that you have multiple threads of execution inside the same application. A thread is like a
separate CPU executing your application. Thus, a multithreaded application is like an application that has multiple CPUs
executing different parts of the code at the same time.
Java is a multi-threaded programming language which means we can develop multi-threaded program using Java. A
multi-threaded program contains two or more parts that can run concurrently and each part can handle a different task at
the same time making optimal use of the available resources specially when your computer has multiple CPUs.
By definition, multitasking is when multiple processes share common processing resources such as a CPU. Multi-threading
extends the idea of multitasking into applications where you can subdivide specific operations within a single
application into individual threads. Each of the threads can run in parallel. The OS divides processing time not only
among different applications, but also among each thread within an application.
Multi-threading enables you to write in a way where multiple activities can proceed concurrently in the same program.

- [Thread](./thread.md)
- [Callable](./callable.md)
- [ExecutorService](./executor_service.md)
- [Future](./future.md)
- [Lock](./lock.md)
- [volatile](./volatile.md)
- [synchronized](./syncronized.md)
- [Thread.sleep()](./sleep.md)
- [wait/notify](./wait_notify.md)
- [Threadsafe collections](./threadsafe_collections.md)
- [Atomics](./atomics.md)
- [Daemon Threads](./daemon_threads.md)
- [deadlock](./deadlock.md)
- [starvation](./starvation.md)
- [race condition](./race_condition.md)
- [context switching](./context_switching.md)
