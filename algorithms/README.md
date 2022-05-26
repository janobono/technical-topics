# Algorithms

An algorithm is a set of instructions for solving a problem or accomplishing a task.

## big O notation (big theta)

Big O notation is a convenient way to describe how fast a function is growing.

When we compute the time complexity T(n) of an algorithm we rarely get an exact result, just an estimate. That’s fine,
in computer science we are typically only interested in how fast T(n) is growing as a function of the input size n.

For example, if an algorithm increments each number in a list of length n, we might say: “This algorithm runs in O(n)
time and performs O(1) work for each element”.

## sorting algorithms

### Insertion sort

Insertion sort is a simple sorting algorithm that is relatively efficient for small lists and mostly sorted lists, and
is often used as part of more sophisticated algorithms. It works by taking elements from the list one by one and
inserting them in their correct position into a new sorted list similar to how we put money in our wallet. In arrays,
the new list and the remaining elements can share the array's space, but insertion is expensive, requiring shifting all
following elements over by one.

### Selection sort

Selection sort is an in-place comparison sort. It has O(n2) complexity, making it inefficient on large lists, and
generally performs worse than the similar insertion sort. Selection sort is noted for its simplicity, and also has
performance advantages over more complicated algorithms in certain situations.

The algorithm finds the minimum value, swaps it with the value in the first position, and repeats these steps for the
remainder of the list. It does no more than n swaps, and thus is useful where swapping is very expensive.

### Bubble sort

A bubble sort, a sorting algorithm that continuously steps through a list, swapping items until they appear in the
correct order.

Bubble sort is a simple sorting algorithm. The algorithm starts at the beginning of the data set. It compares the first
two elements, and if the first is greater than the second, it swaps them. It continues doing this for each pair of
adjacent elements to the end of the data set. It then starts again with the first two elements, repeating until no swaps
have occurred on the last pass.
