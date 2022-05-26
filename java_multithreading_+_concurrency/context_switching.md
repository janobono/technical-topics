# Context switching

The costs include application design, CPU, memory, and context switching. Below are some of the considerations for
concurrency:

- The application design has to be very detailed, covering all possible cases to support concurrency using multiple
  threads. It will be better to cover all corner cases in the design so that developers know how to handle scenarios
  that don't lead the application to a dead-lock or similar issues. Multi-threading makes the application design more
  complex in areas associated with shared data access, read-write locks, and critical sections.
- Context switching — when CPU switches from executing one thread to another, the CPU needs to save local data, program
  pointers, etc. of the current thread. Then, the CPU loads data and the program pointer of the next thread that will be
  executed. This is called context switching, and it uses a lot of CPU cycles if there are too many context switches.
- Context switching is always an overhead, and it is not cheap. It is a resource and CPU intensive process, as the CPU
  has to allocate memory for the thread stack and CPU time for context switches!
