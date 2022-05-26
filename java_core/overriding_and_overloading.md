# Overriding

In any object-oriented programming language, Overriding is a feature that allows a subclass or child class to provide a
specific implementation of a method that is already provided by one of its super-classes or parent classes. When a
method in a subclass has the same name, same parameters or signature, and same return type(or sub-type) as a method in
its super-class, then the method in the subclass is said to override the method in the super-class.

Rules for method overriding:

- Overriding and Access-Modifiers : The access modifier for an overriding method can allow more, but not less, access
  than the overridden method. For example, a protected instance method in the super-class can be made public, but not
  private, in the subclass. Doing so, will generate compile-time error.
- Final methods can not be overridden : If we don’t want a method to be overridden, we declare it as final.
- Static methods can not be overridden(Method Overriding vs Method Hiding) : When you define a static method with same
  signature as a static method in base class, it is known as method hiding.
- Private methods can not be overridden : Private methods cannot be overridden as they are bonded during compile time.
  Therefore we can’t even override private methods in a subclass.
- The overriding method must have same return type (or subtype) : From Java 5.0 onwards it is possible to have different
  return type for a overriding method in child class, but child’s return type should be sub-type of parent’s return
  type. This phenomena is known as covariant return type.
- Invoking overridden method from sub-class : We can call parent class method in overriding method using super keyword.
- Overriding and constructor : We can not override constructor as parent and child class can never have constructor with
  same name(Constructor name must always be same as Class name).
- Overriding and Exception-Handling : Below are two rules to note when overriding methods related to exception-handling.
    * Rule#1 : If the super-class overridden method does not throw an exception, subclass overriding method can only
      throws the unchecked exception, throwing checked exception will lead to compile-time error.
    * Rule#2 : If the super-class overridden method does throws an exception, subclass overriding method can only throw
      same, subclass exception. Throwing parent exception in Exception hierarchy will lead to compile time error.Also
      there is no issue if subclass overridden method is not throwing any exception.
- Overriding and abstract method: Abstract methods in an interface or abstract class are meant to be overridden in
  derived concrete classes otherwise a compile-time error will be thrown.
- Overriding and synchronized/strictfp method : The presence of synchronized/strictfp modifier with method have no
  effect on the rules of overriding, i.e. it’s possible that a synchronized/strictfp method can override a non
  synchronized/strictfp one and vice-versa.

# Overloading

Overloading allows different methods to have the same name, but different signatures where the signature can differ by
the number of input parameters or type of input parameters or both. Overloading is related to compile-time (or static)
polymorphism.

Question Arises:

What if the exact prototype does not match with arguments. Priority wise, compiler take these steps:

- Type Conversion but to higher type(in terms of range) in same family.
- Type conversion to next higher family(suppose if there is no long data type available for an int data type, then it
  will search for the float data type).

What is the advantage?
We don’t have to create and remember different names for functions doing the same thing. For example, in our code, if
overloading was not supported by Java, we would have to create method names like sum1, sum2, … or sum2Int, sum3Int, …
etc.

Can we overload methods on return type?
We cannot overload by return type.

Can we overload static methods?
The answer is ‘Yes’. We can have two ore more static methods with same name, but differences in input parameters.

Can we overload methods that differ only by static keyword?
We cannot overload two methods in Java if they differ only by static keyword (number of parameters and types of
parameters is same).

Can we overload main() in Java?
Like other static methods, we can overload main() in Java. Refer overloading main() in Java for more details.
