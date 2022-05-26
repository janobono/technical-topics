# Generics

In a nutshell, generics enable types (classes and interfaces) to be parameters when defining classes, interfaces and
methods. Much like the more familiar formal parameters used in method declarations, type parameters provide a way for
you to re-use the same code with different inputs. The difference is that the inputs to formal parameters are values,
while the inputs to type parameters are types.
Type Parameter Naming Conventions
By convention, type parameter names are single, uppercase letters. This stands in sharp contrast to the variable naming
conventions that you already know about, and with good reason: Without this convention, it would be difficult to tell
the difference between a type variable and an ordinary class or interface name.
The most commonly used type parameter names are:

- E - Element (used extensively by the Java Collections Framework)
- K - Key
- N - Number
- T - Type
- V - Value
- S,U,V etc. - 2nd, 3rd, 4th types

Generics mean parameterized types. The idea is to allow type (Integer, String, … etc, and user-defined types) to be a
parameter to methods, classes, and interfaces. Using Generics, it is possible to create classes that work with different
data types.
An entity such as class, interface, or method that operates on a parameterized type is called a generic entity.

## Why Generics?

The Object is the superclass of all other classes and Object reference can refer to any type object. These features lack
type safety. Generics add that type safety feature.
Generics in Java is similar to templates in C++. For example, classes like HashSet, ArrayList, HashMap, etc use generics
very well. There are some fundamental differences between the two approaches to generic types.

## Generic Class

We use <> to specify parameter types in generic class creation. To create objects of a generic class, we use the
following syntax class Test<T>{} .

## Generic Functions

We can also write generic functions that can be called with different types of arguments based on the type of arguments
passed to the generic method, the compiler handles each method.
static <T> void genericDisplay (T element){}

## Generics work only with Reference Types

When we declare an instance of a generic type, the type argument passed to the type parameter must be a reference type.
We cannot use primitive data types like int, char.

## Advantages of Generics

Programs that use Generics has got many benefits over non-generic code.

- Code Reuse: We can write a method/class/interface once and use it for any type we want.
- Type Safety: Generics make errors to appear compile time than at run time (It’s always better to know problems in your
  code at compile time rather than making your code fail at run time).
- Generics promotes code reusability.
- Implementing generic algorithms: By using generics, we can implement algorithms that work on different types of
  objects and at the same, they are type safe too.
- Individual Type Casting is not needed: If we do not use generics, then every time we retrieve data from ArrayList, we
  have to typecast it. Typecasting at every retrieval operation is a big headache. If we already know that our list only
  holds string data then we need not typecast it every time.
