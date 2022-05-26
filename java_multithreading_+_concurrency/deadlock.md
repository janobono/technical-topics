# Deadlock

Deadlock describes a situation where two or more threads are blocked forever, waiting for each other. Deadlock occurs
when multiple threads need the same locks but obtain them in different order. A Java multithreaded program may suffer
from the deadlock condition because the synchronized keyword causes the executing thread to block while waiting for the
lock, or monitor, associated with the specified object.

Deadlock: Deadlock is a situation when two threads are waiting for each other and the waiting is never ends. Here both
threads cant completes their tasks.
