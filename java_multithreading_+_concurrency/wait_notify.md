# wait()

Inter-Thread communication is a way by which synchronized threads can communicate with each other using the methods
namely wait(), notify() and notifyAll(). wait() method is a part of java.lang.Object class. When wait() method is
called, the calling thread stops its execution until notify() or notifyAll() method is invoked by some other Thread.

# notify()

The notify() method is defined in the Object class, which is Java’s top-level class. It’s used to wake up only one
thread that’s waiting for an object, and that thread then begins execution. The thread class notify() method is used to
wake up a single thread. If multiple threads are waiting for notification, and we use the notify() method, only one
thread will receive the notification, and the others will have to wait for more. This method does not return any value.

It is used with the wait() method, in order to communicate between the threads as a thread that goes into waiting for
state by wait() method, will be there until any other thread calls either notify() or notifyAll() method.
