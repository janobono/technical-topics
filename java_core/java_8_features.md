# Java 8 features

Some of the important Java 8 features are:

## forEach() method in Iterable interface

Whenever we need to traverse through a Collection, we need to create an Iterator whose whole purpose is to iterate over,
and then we have business logic in a loop for each of the elements in the Collection. We might get
ConcurrentModificationException if the iterator is not used properly.

Java 8 has introduced forEach method in java.lang.Iterable interface so that while writing code we focus on business
logic. The forEach method takes java.util.function.Consumer object as an argument, so it helps in having our business
logic at a separate location that we can reuse.

The number of lines might increase but forEach method helps in having the logic for iteration and business logic at
separate place resulting in higher separation of concern and cleaner code.

## default and static methods in Interfaces

From Java 8, interfaces are enhanced to have a method with implementation. We can use default and static keyword to
create interfaces with method implementation.

If any class in the hierarchy has a method with the same signature, then default methods become irrelevant. The Object
is the base class, so if we have equals(), hashCode() default methods in the interface, it will become irrelevant.
That’s why for better clarity, interfaces are not allowed to have Object default methods.

## Functional Interfaces and Lambda Expressions

Functional interfaces are a new concept introduced in Java 8. An interface with exactly one abstract method becomes a
Functional Interface. We don’t need to use @FunctionalInterface annotation to mark an interface as a Functional
Interface.

@FunctionalInterface annotation is a facility to avoid the accidental addition of abstract methods in the functional
interfaces. You can think of it like @Override annotation and it’s best practice to use it. java.lang.Runnable with a
single abstract method run() is a great example of a functional interface.

One of the major benefits of the functional interface is the possibility to use lambda expressions to instantiate them.
So lambda expressions are a means to create anonymous classes of functional interfaces easily.

A new package java.util.function has been added with bunch of functional interfaces to provide target types for lambda
expressions and method references.

## Java Stream API for Bulk Data Operations on Collections

A new java.util.stream has been added in Java 8 to perform filter/map/reduce like operations with the collection. Stream
API will allow sequential as well as parallel execution.

Collection interface has been extended with stream() and parallelStream() default methods to get the Stream for
sequential and parallel execution.

Notice that parallel processing values are not in order, so parallel processing will be very helpful while working with
huge collections.

## Java Time API

It has always been hard to work with Date, Time, and Time Zones in java. There was no standard approach or API in java
for date and time in Java. One of the nice addition in Java 8 is the java.time package that will streamline the process
of working with time in java.

The new Time API prefers enums over integer constants for months and days of the week. One of the useful classes is
DateTimeFormatter for converting DateTime objects to strings.

## Collection API improvements

Some new methods added in Collection API are:

- Iterator default method forEachRemaining(Consumer action) to perform the given action for each remaining element until
  all elements have been processed or the action throws an exception.
- Collection default method removeIf(Predicate filter) to remove all elements of this collection that satisfy the given
  predicate.
- Collection spliterator() method returning Spliterator instance that can be used to traverse elements sequentially or
  parallel.
- Map replaceAll(), compute(), merge() methods.
- Performance Improvement for HashMap class with Key Collisions

## Concurrency API improvements

Some important concurrent API enhancements are:

- ConcurrentHashMap compute(), forEach(), forEachEntry(), forEachKey(), forEachValue(), merge(), reduce() and search()
  methods.
- CompletableFuture that may be explicitly completed (setting its value and status).
- Executors newWorkStealingPool() method to create a work-stealing thread pool using all available processors as its
  target parallelism level.

## Java IO improvements

Some IO improvements known to me are:

- Files.list(Path dir) that returns a lazily populated Stream, the elements of which are the entries in the directory.
- Files.lines(Path path) that reads all lines from a file as a Stream.
- Files.find() that returns a Stream that is lazily populated with Path by searching for files in a file tree rooted at
  a given starting file.
- BufferedReader.lines() that return a Stream, the elements of which are lines read from this BufferedReader.

## Optional class

Java introduced a new class Optional in jdk8. It is a public final class and used to deal with NullPointerException in
Java application. You must import java.util package to use this class. It provides methods which are used to check the
presence of value for particular variable.

## Miscellaneous Java 8 Core API improvements

Some miscellaneous API improvements that might come handy are:

- ThreadLocal static method withInitial(Supplier supplier) to create instances easily.
- The Comparator interface has been extended with a lot of default and static methods for natural ordering, reverse
  order, etc.
- min(), max() and sum() methods in Integer, Long and Double wrapper classes.
- logicalAnd(), logicalOr() and logicalXor() methods in Boolean class.
- ZipFile.stream() method to get an ordered Stream over the ZIP file entries. Entries appear in the Stream in the order
  they appear in the central directory of the ZIP file.
- Several utility methods in Math class.
- jjs command is added to invoke Nashorn Engine.
- jdeps command is added to analyze class files
- JDBC-ODBC Bridge has been removed.
- PermGen memory space has been removed
