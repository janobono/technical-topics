# Future

A Java Future, java.util.concurrent.Future, represents the result of an asynchronous computation. When the asynchronous
task is created, a Java Future object is returned. This Future object functions as a handle to the result of the
asynchronous task. Once the asynchronous task completes, the result can be accessed via the Future object returned when
the task was started.

```java
public interface Future<V> {

    boolean cancel(boolean mayInterruptIfRunning)

    V get();

    V get(long timeout, TimeUnit unit);

    boolean isCancelled();

    boolean isDone();
}
```
