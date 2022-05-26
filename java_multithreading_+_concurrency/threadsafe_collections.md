# Threadsafe collections

The collections framework is a key component of Java. It provides an extensive number of interfaces and implementations,
which allows us to create and manipulate different types of collections in a straightforward manner.

Although using plain unsynchronized collections is simple overall, it can also become a daunting and error-prone process
when working in multi-threaded environments (a.k.a. concurrent programming).

Hence, the Java platform provides strong support for this scenario through different synchronization wrappers
implemented within the Collections class.

These wrappers make it easy to create synchronized views of the supplied collections by means of several static factory
methods.

## The synchronizedCollection() Method

The first synchronization wrapper that we'll cover in this round-up is the synchronizedCollection() method. As the name
suggests, it returns a thread-safe collection backed up by the specified Collection.

## The synchronizedList() Method

Likewise, similar to the synchronizedCollection() method, we can use the synchronizedList() wrapper to create a
synchronized List. As we might expect, the method returns a thread-safe view of the specified List. The use of the
synchronized block ensures the atomicity of the operation.

## The synchronizedMap() Method

The Collections class implements another neat synchronization wrapper, called synchronizedMap(). We could use it for
easily creating a synchronized Map. The method returns a thread-safe view of the supplied Map implementation.

## The synchronizedSortedMap() Method

There's also a counterpart implementation of the synchronizedMap() method. It is called synchronizedSortedMap(), which
we can use for creating a synchronized SortedMap instance.

## The synchronizedSortedSet() Method

Finally, the last synchronization wrapper that we'll showcase here is synchronizedSortedSet(). Similar to other wrapper
implementations that we've reviewed so far, the method returns a thread-safe version of the given SortedSet.

## Synchronized Collections

Synchronized collections achieve thread-safety through intrinsic locking, and the entire collections are locked.
Intrinsic locking is implemented via synchronized blocks within the wrapped collection's methods.

As we might expect, synchronized collections assure data consistency/integrity in multi-threaded environments. However,
they might come with a penalty in performance, as only one single thread can access the collection at a time (a.k.a.
synchronized access).

## Concurrent Collections

Concurrent collections (e.g. ConcurrentHashMap), achieve thread-safety by dividing their data into segments. In a
ConcurrentHashMap, for example, different threads can acquire locks on each segment, so multiple threads can access the
Map at the same time (a.k.a. concurrent access).

Concurrent collections are much more performant than synchronized collections, due to the inherent advantages of
concurrent thread access.

So, the choice of what type of thread-safe collection to use depends on the requirements of each use case, and it should
be evaluated accordingly.
