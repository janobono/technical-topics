# OOP

Object-oriented programming combines a group of data attributes with functions or methods into a unit called an "
object." Typically, OOP languages are class-based, which means that a class defines the data attributes and functions as
a blueprint for creating objects, which are instances of the class.

## OOP terms

### Object

Let us understand this with an example. Consider your mobile phone as an object. There can be different properties for
your mobile phone like its model, software version, and memory in it. This object can also have functions like switch on
the camera, turn off Bluetooth, restart, etc. In simple words, each object contains data and instructions to act on that
data.

### Class

This is another important term in object-oriented programming. A class is like a template from which new objects are
created. Any class you create will always have a head and a body. A head typically includes modifiers and the keyword of
the class while the body includes data members and member functions.

Here are the different components of a class:

- Public - The class members can be accessed from everywhere.
- Private - The class members can only be accessed by the defining class.
- Protected - the class members can only be accessed by parent and inherited classes.

## OOP concepts

The basic principles of OOP involves Abstraction, Encapsulation, Inheritance, and Polymorphism. There are also objects
and classes. Together, they stand as the working principle of any object-oriented programming language.

### Abstraction

Abstraction allows you to create seamless programs by just knowing what method to call and what parameters to input.

Often, it’s easier to reason and design a program when you can separate the interface of a class from its
implementation, and focus on the interface. This is akin to treating a system as a “black box,” where it’s not important
to understand the gory inner workings in order to reap the benefits of using it.

This process is called “abstraction” in OOP, because we are abstracting away the gory implementation details of a class
and only presenting a clean and easy-to-use interface via the class member functions. Carefully used, abstraction helps
isolate the impact of changes made to the code, so that if something goes wrong, the change will only affect the
implementation details of a class and not the outside code.

### Encapsulation

It is a group of properties and members under a single class or Object. Programs can be really long and there can easily
be a ton of moving parts in it. After some time it gets really tough to maintain all these objects without them running
into complexity.

This is where a primary principle like encapsulation comes into play. You can use this principle to encapsulate a set of
objects into different classes. With this principle, you can prevent the repetition of code and also shorten the length
of your code.

The word, “encapsulate,” means to enclose something. Just like a pill "encapsulates" or contains the medication inside
of its coating, the principle of encapsulation works in a similar way in OOP: by forming a protective barrier around the
information contained within a class from the rest of the code.

In OOP, we encapsulate by binding the data and functions which operate on that data into a single unit, the class. By
doing so, we can hide private details of a class from the outside world and only expose functionality that is important
for interfacing with it. When a class does not allow calling code access to its private data directly, we say that it is
well encapsulated.

### Inheritance

It is the ability to acquire the properties of existing classes and create new ones. Inheritance allows you to reuse
code without having to rewrite it in a program. One of the best features of Inheritance is the ability to shorten the
code in a program. You can use this principle to inherit codes from another class and reuse it in a new class.

### Polymorphism

In OOP, polymorphism allows for the uniform treatment of classes in a hierarchy. Therefore, calling code only needs to
be written to handle objects from the root of the hierarchy, and any object instantiated by any child class in the
hierarchy will be handled in the same way.

Because derived objects share the same interface as their parents, the calling code can call any function in that class’
interface. At run-time, the appropriate function will be called depending on the type of object passed leading to
possibly different behaviors.

Polymorphism refers to one name with many forms. It is the ability of one function to perform in different ways. In
other words, it refers to an object’s ability to take on more than one single form.

Polymorphism can be applied in two simple ways:

#### method overloading

When a class has multiple methods with the same names but a different set of parameters, it is called Method
overloading. You can proceed with method overloading, only if your methods satisfy any one of the following rules:

- has different parameters
- has different return types
- has different access modifiers.

#### method overriding

The second way to go ahead with polymorphism is method overriding. This is only possible if a subclass ( or ) sister
class has the same method as the parent class. Much like Method overloading, there are also some rules for method
overriding to work.

- has the same parameter list
- has the same return type
- and should have an access modifier that more restrictive than that of the parent class.
