# Java Memory Model

The Java memory model specifies how the Java virtual machine works with the computer's memory (RAM). The Java virtual
machine is a model of a whole computer so this model naturally includes a memory model - AKA the Java memory model.

To run an application in an optimal way, JVM divides memory into stack and heap memory. Whenever we declare new
variables and objects, call a new method, declare a String, or perform similar operations, JVM designates memory to
these operations from either Stack Memory or Heap Space.

## heap

Heap space is used for the dynamic memory allocation of Java objects and JRE classes at runtime. New objects are always
created in heap space, and the references to these objects are stored in stack memory.

These objects have global access and we can access them from anywhere in the application.

We can break this memory model down into smaller parts, called generations, which are:

- Young Generation – this is where all new objects are allocated and aged. A minor Garbage collection occurs when this
  fills up.
- Old or Tenured Generation – this is where long surviving objects are stored. When objects are stored in the Young
  Generation, a threshold for the object's age is set, and when that threshold is reached, the object is moved to the
  old generation.
- Permanent Generation – this consists of JVM metadata for the runtime classes and application methods.

### Key Features of Java Heap Memory

Some other features of heap space include:

- It's accessed via complex memory management techniques that include the Young Generation, Old or Tenured Generation,
  and Permanent Generation.
- If heap space is full, Java throws java.lang.OutOfMemoryError.
- Access to this memory is comparatively slower than stack memory
- This memory, in contrast to stack, isn't automatically deallocated. It needs Garbage Collector to free up unused
  objects so as to keep the efficiency of the memory usage.
- Unlike stack, a heap isn't threadsafe and needs to be guarded by properly synchronizing the code.

## stack

Stack Memory in Java is used for static memory allocation and the execution of a thread. It contains primitive values
that are specific to a method and references to objects referred from the method that are in a heap.

Access to this memory is in Last-In-First-Out (LIFO) order. Whenever we call a new method, a new block is created on top
of the stack which contains values specific to that method, like primitive variables and references to objects.

When the method finishes execution, its corresponding stack frame is flushed, the flow goes back to the calling method,
and space becomes available for the next method.

### Key Features of Stack Memory

Some other features of stack memory include:

- It grows and shrinks as new methods are called and returned, respectively.
- Variables inside the stack exist only as long as the method that created them is running.
- It's automatically allocated and deallocated when the method finishes execution.
- If this memory is full, Java throws java.lang.StackOverFlowError.
- Access to this memory is fast when compared to heap memory.
- This memory is threadsafe, as each thread operates in its own stack.

## permgen/metaspace

### PermGen

PermGen (Permanent Generation) is a special heap space separated from the main memory heap.

The JVM keeps track of loaded class metadata in the PermGen. Additionally, the JVM stores all the static content in this
memory section. This includes all the static methods, primitive variables, and references to the static objects.

Furthermore, it contains data about bytecode, names, and JIT information. Before Java 7, the String Pool was also part
of this memory. The disadvantages of the fixed pool size are listed in our write-up.

The default maximum memory size for 32-bit JVM is 64 MB and 82 MB for the 64-bit version.

However, we can change the default size with the JVM options:

- -XX:PermSize=[size] is the initial or minimum size of the PermGen space
- -XX:MaxPermSize=[size] is the maximum size

Most importantly, Oracle completely removed this memory space in the JDK 8 release. Therefore, if we use these tuning
flags in Java 8 and newer versions, we'll get the following warnings:

```shell
java -XX:PermSize=100m -XX:MaxPermSize=200m -version

OpenJDK 64-Bit Server VM warning: Ignoring option PermSize; support was removed in 8.0
OpenJDK 64-Bit Server VM warning: Ignoring option MaxPermSize; support was removed in 8.0
```

With its limited memory size, PermGen is involved in generating the famous OutOfMemoryError. Simply put, the class
loaders weren't garbage collected properly and, as a result, generated a memory leak.

Therefore, we receive a memory space error; this happens mostly in the development environment while creating new class
loaders.

### Metaspace

Simply put, Metaspace is a new memory space – starting from the Java 8 version; it has replaced the older PermGen memory
space. The most significant difference is how it handles memory allocation.

Specifically, this native memory region grows automatically by default.

We also have new flags to tune the memory:

- MetaspaceSize and MaxMetaspaceSize – we can set the Metaspace upper bounds.
- MinMetaspaceFreeRatio – is the minimum percentage of class metadata capacity free after garbage collection
- MaxMetaspaceFreeRatio – is the maximum percentage of class metadata capacity free after a garbage collection to avoid
  a reduction in the amount of space
- Additionally, the garbage collection process also gains some benefits from this change. The garbage collector now
  automatically triggers the cleaning of the dead classes once the class metadata usage reaches its maximum metaspace
  size.
- Therefore, with this improvement, JVM reduces the chance to get the OutOfMemory error.
- Despite all of these improvements, we still need to monitor and tune the metaspace to avoid memory leaks.

## garbage collectors in Java

From the name, it looks like Garbage Collection deals with finding and deleting the garbage from memory. However, in
reality, Garbage Collection tracks each and every object available in the JVM heap space and removes unused ones.

In simple words, GC works in two simple steps known as Mark and Sweep:

- Mark – it is where the garbage collector identifies which pieces of memory are in use and which are not
- Sweep – this step removes objects identified during the “mark” phase

Advantages:

- No manual memory allocation/deallocation handling because unused memory space is automatically handled by GC
- No overhead of handling Dangling Pointer
- Automatic Memory Leak management (GC on its own can't guarantee the full proof solution to memory leaking, however, it
  takes care of a good portion of it)

Disadvantages:

- Since JVM has to keep track of object reference creation/deletion, this activity requires more CPU power than the
  original application. It may affect the performance of requests which required large memory
- Programmers have no control over the scheduling of CPU time dedicated to freeing objects that are no longer needed
- Using some GC implementations might result in application stopping unpredictably
- Automatized memory management will not be as efficient as the proper manual memory allocation/deallocation

### GC Implementations

JVM has five types of GC implementations:

- Serial Garbage Collector
- Parallel Garbage Collector
- CMS Garbage Collector
- G1 Garbage Collector
- Z Garbage Collector

#### Serial Garbage Collector

This is the simplest GC implementation, as it basically works with a single thread. As a result, this GC implementation
freezes all application threads when it runs. Hence, it is not a good idea to use it in multi-threaded applications like
server environments.

However, there was an excellent talk by Twitter engineers at QCon 2012 on the performance of Serial Garbage Collector –
which is a good way to understand this collector better.

The Serial GC is the garbage collector of choice for most applications that do not have small pause time requirements
and run on client-style machines. To enable Serial Garbage Collector, we can use the following argument:

```shell
java -XX:+UseSerialGC -jar Application.java
```

#### Parallel Garbage Collector

It's the default GC of the JVM and sometimes called Throughput Collectors. Unlike Serial Garbage Collector, this uses
multiple threads for managing heap space. But it also freezes other application threads while performing GC.

If we use this GC, we can specify maximum garbage collection threads and pause time, throughput, and footprint (heap
size).

The numbers of garbage collector threads can be controlled with the command-line option -XX:ParallelGCThreads=<N>.

The maximum pause time goal (gap [in milliseconds] between two GC) is specified with the command-line option -XX:
MaxGCPauseMillis=<N>.

The time spent doing garbage collection versus the time spent outside of garbage collection is called the maximum
throughput target and can be specified by the command-line option -XX:GCTimeRatio=<N>.

The maximum heap footprint (the amount of heap memory that a program requires while running) is specified using the
option -Xmx<N>.

To enable Parallel Garbage Collector, we can use the following argument:

```shell
java -XX:+UseParallelGC -jar Application.java
```

#### CMS Garbage Collector

The Concurrent Mark Sweep (CMS) implementation uses multiple garbage collector threads for garbage collection. It's
designed for applications that prefer shorter garbage collection pauses, and that can afford to share processor
resources with the garbage collector while the application is running.

Simply put, applications using this type of GC respond slower on average but do not stop responding to perform garbage
collection.

A quick point to note here is that since this GC is concurrent, an invocation of explicit garbage collection such as
using System.gc() while the concurrent process is working, will result in Concurrent Mode Failure / Interruption.

If more than 98% of the total time is spent in CMS garbage collection and less than 2% of the heap is recovered, then an
OutOfMemoryError is thrown by the CMS collector. If necessary, this feature can be disabled by adding the option -XX:
-UseGCOverheadLimit to the command line.

This collector also has a mode knows as an incremental mode which is being deprecated in Java SE 8 and may be removed in
a future major release.

To enable the CMS Garbage Collector, we can use the following flag:

```shell
java -XX:+UseParNewGC -jar Application.java
```

As of Java 9, the CMS garbage collector has been deprecated. Therefore, JVM prints a warning message if we try to use
it:

```shell
java -XX:+UseConcMarkSweepGC --version
```

Java HotSpot(TM) 64-Bit Server VM warning: Option UseConcMarkSweepGC was deprecated

in version 9.0 and will likely be removed in a future release.

java version "9.0.1"

Moreover, Java 14 completely dropped the CMS support:

```shell
java -XX:+UseConcMarkSweepGC --version
```

OpenJDK 64-Bit Server VM warning: Ignoring option UseConcMarkSweepGC;

support was removed in 14.0

openjdk 14 2020-03-17

#### G1 Garbage Collector

G1 (Garbage First) Garbage Collector is designed for applications running on multi-processor machines with large memory
space. It's available since JDK7 Update 4 and in later releases.

G1 collector will replace the CMS collector since it's more performance efficient.

Unlike other collectors, the G1 collector partitions the heap into a set of equal-sized heap regions, each a contiguous
range of virtual memory. When performing garbage collections, G1 shows a concurrent global marking phase (i.e. phase 1
known as Marking) to determine the liveness of objects throughout the heap.

After the mark phase is completed, G1 knows which regions are mostly empty. It collects in these areas first, which
usually yields a significant amount of free space (i.e. phase 2 known as Sweeping). It is why this method of garbage
collection is called Garbage-First.

To enable the G1 Garbage Collector, we can use the following argument:

```shell
java -XX:+UseG1GC -jar Application.java
```

#### Java 8 Changes

Java 8u20 has introduced one more JVM parameter for reducing the unnecessary use of memory by creating too many
instances of the same String. This optimizes the heap memory by removing duplicate String values to a global single
char[] array.

This parameter can be enabled by adding -XX:+UseStringDeduplication as a JVM parameter.

#### Z Garbage Collector

ZGC (Z Garbage Collector) is a scalable low-latency garbage collector which debuted in Java 11 as an experimental option
for Linux. JDK 14 introduced ZGC under the Windows and macOS operating systems. ZGC has obtained the production status
from Java 15 onwards.

ZGC performs all expensive work concurrently, without stopping the execution of application threads for more than 10 ms,
which makes it suitable for applications that require low latency. It uses load barriers with colored pointers to
perform concurrent operations when the threads are running and they are used to keep track of heap usage.

Reference coloring (colored pointers) is the core concept of ZGC. It means that ZGC uses some bits (metadata bits) of
reference to mark the state of the object. It also handles heaps ranging from 8MB to 16TB in size. Furthermore, pause
times do not increase with the heap, live-set, or root-set size.

Similar to G1, Z Garbage Collector partitions the heap, except that heap regions can have different sizes.

To enable the Z Garbage Collector, we can use the following argument in JDK versions lower than 15:

```shell
java -XX:+UnlockExperimentalVMOptions -XX:+UseZGC Application.java
```

From version 15 we don't need experimental mode on:

```shell
java -XX:+UseZGC Application.java
```

We should note that ZGC is not the default Garbage Collector.

## happens before

The Java happens before guarantee is a set of rules that govern how the Java VM and CPU is allowed to reorder
instructions for performance gains. The happens before guarantee makes it possible for threads to rely on when a
variable value is synchronized to or from main memory, and which other variables have been synchronized at the same
time. The Java happens before guarantee are centered around access to volatile variables and variables accessed from
within synchronized blocks.

## JIT compiler

When we compile our Java program (e.g., using the javac command), we'll end up with our source code compiled into the
binary representation of our code – a JVM bytecode. This bytecode is simpler and more compact than our source code, but
conventional processors in our computers cannot execute it.

To be able to run a Java program, the JVM interprets the bytecode. Since interpreters are usually a lot slower than
native code executing on a real processor, the JVM can run another compiler which will now compile our bytecode into the
machine code that can be run by the processor. This so-called just-in-time compiler is much more sophisticated than the
javac compiler, and it runs complex optimizations to generate high-quality machine code.
