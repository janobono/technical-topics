# Mutable vs Immutable

Java is an object-oriented programming language. As it is an object-oriented programming language, it's all methods and
mechanism revolves around the objects. One object-based concept is mutable and immutable in Java.

Objects in Java are either mutable or immutable; it depends on how the object can be iterated.

## Mutable objects

The mutable objects are objects whose value can be changed after initialization. We can change the object's values, such
as field and states, after the object is created. For example, Java.util.Date, StringBuilder, StringBuffer, etc.

When we made a change in existing mutable objects, no new object will be created; instead, it will alter the value of
the existing object. These object's classes provide methods to make changes in it. The Getters and Setters ( get() and
set() methods ) are available in mutable objects. The Mutable object may or may not be thread-safe.

## Immutable Objects

The immutable objects are objects whose value can not be changed after initialization. We can not change anything once
the object is created. For example, primitive objects such as int, long, float, double, all legacy classes, Wrapper
class, String class, etc.

In a nutshell, immutable means unmodified or unchangeable. Once the immutable objects are created, its object values and
state can not be changed.

Only Getters ( get() method) are available not Setters ( set() method) for immutable objects.

## Key difference between mutable and immutable objects in Java

- The mutable objects can be changed to any value or state without adding a new object. Whereas, the immutable objects
  can not be changed to its value or state once it is created. In the case of immutable objects, whenever we change the
  state of the object, a new object will be created.
- Mutable objects provide a method to change the content of the object. Comparatively, the immutable objects do not
  provide any method to change the values.
- The mutable objects support the setters and getters both. Comparatively, the immutable objects support only getters,
  not setters.
- The Mutable objects are may or may not be thread-safe, but the immutable objects are thread-safe by default.
- The mutable class examples are StringBuffer, Java.util.Date, StringBuilder, etc. Whereas the immutable objects are
  legacy classes, wrapper classes, String class, etc.
