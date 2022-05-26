# Object Class

The Object class is the parent class of all the classes in java by default. In other words, it is the topmost class of
java. The Object class is beneficial if you want to refer any object whose type you don't know. Notice that parent class
reference variable can refer the child class object, know as upcasting. The Object class provides some common behaviors
to all the objects such as object can be compared, object can be cloned, object can be notified etc.
Object class is present in java.lang package. Every class in Java is directly or indirectly derived from the Object
class. If a Class does not extend any other class then it is direct child class of Object and if extends other class
then it is an indirectly derived. Therefore the Object class methods are available to all Java classes. Hence Object
class acts as a root of inheritance hierarchy in any Java Program.

## Using Object class methods

There are methods in Object class:

- toString() : toString() provides String representation of an Object and used to convert an object to String. The
  default toString() method for class Object returns a string consisting of the name of the class of which the object is
  an instance, the at-sign character `@’, and the unsigned hexadecimal representation of the hash code of the object. It
  is always recommended to override toString() method to get our own String representation of Object.
- hashCode() : For every object, JVM generates a unique number which is hashcode. It returns distinct integers for
  distinct objects. A common misconception about this method is that hashCode() method returns the address of object,
  which is not correct. It converts the internal address of object to an integer by using an algorithm. The hashCode()
  method is native because in Java it is impossible to find address of an object, so it uses native languages like C/C++
  to find address of the object. Use of hashCode() method : Returns a hash value that is used to search object in a
  collection. JVM(Java Virtual Machine) uses hashcode method while saving objects into hashing related data structures
  like HashSet, HashMap, Hashtable etc. The main advantage of saving objects based on hash code is that searching
  becomes easy.
- equals(Object obj) : Compares the given object to “this” object (the object on which the method is called). It gives a
  generic way to compare objects for equality. It is recommended to override equals(Object obj) method to get our own
  equality condition on Objects. It is generally necessary to override the hashCode() method whenever this method is
  overridden, so to maintain the general contract for the hashCode method, which states that equal objects must have
  equal hash codes.
- getClass() : Returns the class object of “this” object and used to get actual runtime class of the object. It can also
  be used to get metadata of this class. The returned Class object is the object that is locked by static synchronized
  methods of the represented class. As it is final so we don’t override it. After loading a .class file, JVM will create
  an object of the type java.lang.Class in the Heap area. We can use this class object to get Class level information.
  It is widely used in Reflection
- finalize() method : This method is called just before an object is garbage collected. It is called by the Garbage
  Collector on an object when garbage collector determines that there are no more references to the object. We should
  override finalize() method to dispose system resources, perform clean-up activities and minimize memory leaks. For
  example before destroying Servlet objects web container, always called finalize method to perform clean-up activities
  of the session. Finalize method is called just once on an object even though that object is eligible for garbage
  collection multiple times.
- clone() : It returns a new object that is exactly the same as this object. For clone() method refer Clone()
- The remaining three methods wait(), notify() notifyAll() are related to Concurrency.
