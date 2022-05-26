# Lock

A lock is a thread synchronization mechanism like synchronized blocks except locks can be more sophisticated than Java's
synchronized blocks. Locks (and other more advanced synchronization mechanisms) are created using synchronized blocks,
so it is not like we can get totally rid of the synchronized keyword.

From Java 5 the package java.util.concurrent.locks contains several lock implementations, so you may not have to
implement your own locks. But you will still need to know how to use them, and it can still be useful to know the theory
behind their implementation.

```java
public class Lock {

    private boolean isLocked = false;

    public synchronized void lock() throws InterruptedException {
        while (isLocked) {
            wait();
        }
        isLocked = true;
    }


    public synchronized void unlock() {
        isLocked = false;
        notify();
    }
}
```

```java
public class UseLock {

    public void use() {
        lock.lock();
        try {
            //do critical section code, which may throw exception
        } finally {
            lock.unlock();
        }
    }
}
```
