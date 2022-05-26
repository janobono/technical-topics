# Thread

There are two ways to create a thread:

- By extending Thread class
- By implementing Runnable interface.

## Thread class

Thread class provide constructors and methods to create and perform operations on a thread.Thread class extends Object
class and implements Runnable interface.
Commonly used Constructors of Thread class:

- Thread()
- Thread(String name)
- Thread(Runnable r)
- Thread(Runnable r,String name)

Commonly used methods of Thread class:

- public void run(): is used to perform action for a thread.
- public void start(): starts the execution of the thread.JVM calls the run() method on the thread.
- public void sleep(long miliseconds): Causes the currently executing thread to sleep (temporarily cease execution) for
  the specified number of milliseconds.
- public void join(): waits for a thread to die.
- public void join(long miliseconds): waits for a thread to die for the specified miliseconds.
- public int getPriority(): returns the priority of the thread.
- public int setPriority(int priority): changes the priority of the thread.
- public String getName(): returns the name of the thread.
- public void setName(String name): changes the name of the thread.
- public Thread currentThread(): returns the reference of currently executing thread.
- public int getId(): returns the id of the thread.
- public Thread.State getState(): returns the state of the thread.
- public boolean isAlive(): tests if the thread is alive.
- public void yield(): causes the currently executing thread object to temporarily pause and allow other threads to
  execute.
- public void suspend(): is used to suspend the thread(depricated).
- public void resume(): is used to resume the suspended thread(depricated).
- public void stop(): is used to stop the thread(depricated).
- public boolean isDaemon(): tests if the thread is a daemon thread.
- public void setDaemon(boolean b): marks the thread as daemon or user thread.
- public void interrupt(): interrupts the thread.
- public boolean isInterrupted(): tests if the thread has been interrupted.
- public static boolean interrupted(): tests if the current thread has been interrupted.

## Runnable interface

The Runnable interface should be implemented by any class whose instances are intended to be executed by a thread.
Runnable interface have only one method named run().

- public void run(): is used to perform action for a thread.

```java
public class EventLoggingTask implements Runnable {
    private Logger logger = LoggerFactory.getLogger(EventLoggingTask.class);

    @Override
    public void run() {
        logger.info("Message");
    }
}
```

```java
public class TaskExecutor {
    public void executeTask() {
        executorService = Executors.newSingleThreadExecutor();
        Future future = executorService.submit(new EventLoggingTask());
        executorService.shutdown();
    }
}
```

## Starting a thread

The start() method of Thread class is used to start a newly created thread. It performs the following tasks:

- A new thread starts(with new callstack).
- The thread moves from New state to the Runnable state.
- When the thread gets a chance to execute, its target run() method will run.
