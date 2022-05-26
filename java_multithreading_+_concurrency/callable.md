# Callable

The Java Callable interface, java.util.concurrent.Callable, represents an asynchronous task which can be executed by a
separate thread. For instance, it is possible to submit a Callable object to a Java ExecutorService which will then
execute it asynchronously.
The Java Callable interface is quite simple. It contains a single method named call(). The call() method is called in
order to execute the asynchronous task. The call() method can return a result. If the task is executed asynchronously,
the result is typically propagated back to the creator of the task via a Java Future. This is the case when a Callable
is submitted to an ExecutorService for concurrent execution. The call() method can also thrown an Exception in case the
task fails during execution.

```java
public class FactorialTask implements Callable<Integer> {
    int number;

    // standard constructors

    public Integer call() throws InvalidParamaterException {
        int fact = 1;
        // ...
        for (int count = number; count > 1; count--) {
            fact = fact * count;
        }

        return fact;
    }
}
```

```java
public class TaskTest {

    @Test
    public void whenTaskSubmitted_ThenFutureResultObtained() {
        FactorialTask task = new FactorialTask(5);
        Future<Integer> future = executorService.submit(task);

        assertEquals(120, future.get().intValue());
    }
}
```
