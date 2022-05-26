# Stream API

The addition of the Stream was one of the major features added to Java 8. First of all, Java 8 Streams should not be
confused with Java I/O streams (ex: FileInputStream etc); these have very little to do with each other.

Simply put, streams are wrappers around a data source, allowing us to operate with that data source and making bulk
processing convenient and fast.

A stream does not store data and, in that sense, is not a data structure. It also never modifies the underlying data
source.

This functionality - java.util.stream - supports functional-style operations on streams of elements, such as map-reduce
transformations on collections.

## Java Stream Creation

Java 8 added a new stream() method to the Collection interface, and we can create a stream from individual objects using
Stream.of() or simply using Stream.builder().

## Java Stream Operations

### forEach

forEach() is simplest and most common operation; it loops over the stream elements, calling the supplied function on
each element. The method is so common that is has been introduced directly in Iterable, Map etc.

forEach() is a terminal operation, which means that, after the operation is performed, the stream pipeline is considered
consumed, and can no longer be used.

### map

map() produces a new stream after applying a function to each element of the original stream. The new stream could be of
different type.

### collect

collect() performs mutable fold operations (repackaging elements to some data structures and applying some additional
logic, concatenating them, etc.) on data elements held in the Stream instance.

The strategy for this operation is provided via the Collector interface implementation. In the example above, we used
the toList collector to collect all Stream elements into a List instance.

### filter

filter() produces a new stream that contains elements of the original stream that pass a given test (specified by a
Predicate).

### findFirst

findFirst() returns an Optional for the first entry in the stream; the Optional can, of course, be empty.

### toArray

If we need to get an array out of the stream, we can simply use toArray().

### flatMap

A stream can hold complex data structures like Stream<List<String>>. In cases like this, flatMap() helps us to flatten
the data structure to simplify further operations.

Notice how we were able to convert the Stream<List<String>> to a simpler Stream<String> - using the flatMap() API.

### peek

Sometimes we need to perform multiple operations on each element of the stream before any terminal operation is applied.

peek() can be useful in situations like this. Simply put, it performs the specified operation on each element of the
stream and returns a new stream which can be used further. peek() is an intermediate operation.

### Method Types and Pipelines

As we’ve been discussing, Java stream operations are divided into intermediate and terminal operations.

Intermediate operations such as filter() return a new stream on which further processing can be done. Terminal
operations, such as forEach(), mark the stream as consumed, after which point it can no longer be used further.

A stream pipeline consists of a stream source, followed by zero or more intermediate operations, and a terminal
operation.

Some operations are deemed short-circuiting operations. Short-circuiting operations allow computations on infinite
streams to complete in finite time.

### Lazy Evaluation

One of the most important characteristics of Java streams is that they allow for significant optimizations through lazy
evaluations.

Computation on the source data is only performed when the terminal operation is initiated, and source elements are
consumed only as needed.

All intermediate operations are lazy, so they’re not executed until a result of a processing is actually needed.

### Comparison Based Stream Operations

#### sorted

sorted() operation - this sorts the stream elements based on the comparator passed we pass into it.

#### min and max

As the name suggests, min() and max() return the minimum and maximum element in the stream respectively, based on a
comparator. They return an Optional since a result may or may not exist (due to, say, filtering). We can also avoid
defining the comparison logic by using Comparator.comparing().

#### distinct

distinct() does not take any argument and returns the distinct elements in the stream, eliminating duplicates. It uses
the equals() method of the elements to decide whether two elements are equal or not.

#### allMatch, anyMatch, and noneMatch

These operations all take a predicate and return a boolean. Short-circuiting is applied and processing is stopped as
soon as the answer is determined.

- allMatch() checks if the predicate is true for all the elements in the stream.
- anyMatch() checks if the predicate is true for any one element in the stream.
- noneMatch() checks if there are no elements matching the predicate.

### Java Stream Specializations

Stream is a stream of object references. However, there are also the IntStream, LongStream, and DoubleStream - which are
primitive specializations for int, long and double respectively. These are quite convenient when dealing with a lot of
numerical primitives.

These specialized streams do not extend Stream but extend BaseStream on top of which Stream is also built.

As a consequence, not all operations supported by Stream are present in these stream implementations. For example, the
standard min() and max() take a comparator, whereas the specialized streams do not.

Specialized streams provide additional operations as compared to the standard Stream - which are quite convenient when
dealing with numbers. For example sum(), average(), range() etc.

### Reduction Operations

A reduction operation (also called as fold) takes a sequence of input elements and combines them into a single summary
result by repeated application of a combining operation. We already saw few reduction operations like findFirst(), min()
and max().

#### reduce

The most common form of reduce() is:

T reduce(T identity, BinaryOperator<T> accumulator)

where identity is the starting value and accumulator is the binary operation we repeated apply.

#### partitioningBy

We can partition a stream into two - based on whether the elements satisfy certain criteria or not.

#### groupingBy

groupingBy() offers advanced partitioning – where we can partition the stream into more than just two groups.

It takes a classification function as its parameter. This classification function is applied to each element of the
stream.

The value returned by the function is used as a key to the map that we get from the groupingBy collector.

#### mapping

Sometimes we might need to group data into a type other than the element type. Here’s how we can do that; we can use
mapping() which can actually adapt the collector to a different type – using a mapping function.

#### reducing

reducing() is similar to reduce() - which we explored before. It simply returns a collector which performs a reduction
of its input elements.

### Parallel Streams

Using the support for parallel streams, we can perform stream operations in parallel without having to write any
boilerplate code; we just have to designate the stream as parallel.

This functionality can, of course, be tuned and configured further, if you need more control over the performance
characteristics of the operation.

As is the case with writing multi-threaded code, we need to be aware of few things while using parallel streams:

- We need to ensure that the code is thread-safe. Special care needs to be taken if the operations performed in parallel
  modifies shared data.
- We should not use parallel streams if the order in which operations are performed or the order returned in the output
  stream matters. For example operations like findFirst() may generate the different result in case of parallel streams.
- Also, we should ensure that it is worth making the code execute in parallel. Understanding the performance
  characteristics of the operation in particular, but also of the system as a whole – is naturally very important here.

### Infinite Streams

Sometimes, we might want to perform operations while the elements are still getting generated. We might not know
beforehand how many elements we’ll need. Unlike using list or map, where all the elements are already populated, we can
use infinite streams, also called as unbounded streams.

### generate

We provide a Supplier to generate() which gets called whenever new stream elements need to be generated. With infinite
streams, we need to provide a condition to eventually terminate the processing. One common way of doing this is using
limit().

Please note that the Supplier passed to generate() could be stateful and such stream may not produce the same result
when used in parallel.

### iterate

iterate() takes two parameters: an initial value, called seed element and a function which generates next element using
the previous value. iterate(), by design, is stateful and hence may not be useful in parallel streams.
