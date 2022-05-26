# ExecutorService

The Java ExecutorService interface, java.util.concurrent.ExecutorService, represents an asynchronous execution mechanism
which is capable of executing tasks concurrently in the background. The Java ExecutorService is very similar to a thread
pool. In fact, the implementation of the ExecutorService interface present in the java.util.concurrent package is a
thread pool implementation.
Since ExecutorService is an interface, you need to its implementations in order to make any use of it. The
ExecutorService has the following implementation in the java.util.concurrent package:

- ThreadPoolExecutor
- ScheduledThreadPoolExecutor

## Execute Runnable

The Java ExecutorService execute(Runnable) method takes a java.lang.Runnable object, and executes it asynchronously.
Here is an example of executing a Runnable with an ExecutorService. There is no way of obtaining the result of the
executed Runnable, if necessary. You will have to use a Callable for that (explained in the following sections).

## Submit Runnable

The Java ExecutorService submit(Runnable) method also takes a Runnable implementation, but returns a Future object. This
Future object can be used to check if the Runnable has finished executing. The submit() method returns a Java Future
object which can be used to check when the Runnable has completed.

## Submit Callable

The Java ExecutorService submit(Callable) method is similar to the submit(Runnable) method except it takes a Java
Callable instead of a Runnable. The Callable's result can be obtained via the Java Future object returned by the submit(
Callable) method.

## invokeAny()

The invokeAny() method takes a collection of Callable objects, or subinterfaces of Callable. Invoking this method does
not return a Future, but returns the result of one of the Callable objects. You have no guarantee about which of the
Callable's results you get. Just one of the ones that finish. If one Callable finishes, so that a result is returned
from invokeAny(), then the rest of the Callable instances are cancelled. If one of the tasks complete (or throws an
exception), the rest of the Callable's are cancelled.

## invokeAll()

The invokeAll() method invokes all of the Callable objects you pass to it in the collection passed as parameter. The
invokeAll() returns a list of Future objects via which you can obtain the results of the executions of each Callable.
Keep in mind that a task might finish due to an exception, so it may not have "succeeded". There is no way on a Future
to tell the difference.
