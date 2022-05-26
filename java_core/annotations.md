# Annotations

Annotations are used to provide supplemental information about a program.

- Annotations start with ‘@’.
- Annotations do not change the action of a compiled program.
- Annotations help to associate metadata (information) to the program elements i.e. instance variables, constructors,
  methods, classes, etc.
- Annotations are not pure comments as they can change the way a program is treated by the compiler.

## Categories of Annotations

- Marker Annotations - The only purpose is to mark a declaration. These annotations contain no members and do not
  consist of any data. Thus, its presence as an annotation is sufficient. Since the marker interface contains no
  members, simply determining whether it is present or absent is sufficient. @Override is an example of Marker
  Annotation.
- Single value Annotations - These annotations contain only one member and allow a shorthand form of specifying the
  value of the member. We only need to specify the value for that member when the annotation is applied and don’t need
  to specify the name of the member. However, in order to use this shorthand, the name of the member must be a value.
  @TestAnnotation(“testing”)
- Full Annotations - These annotations consist of multiple data members, names, values, pairs. @TestAnnotation(
  owner=”Rahul”, value=”Class Geeks”)
- Type Annotations - These annotations can be applied to any place where a type is being used. For example, we can
  annotate the return type of a method. These are declared annotated with @Target annotation.
- Repeating Annotations - These are the annotations that can be applied to a single item more than once. For an
  annotation to be repeatable it must be annotated with the @Repeatable annotation, which is defined in the
  java.lang.annotation package. Its value field specifies the container type for the repeatable annotation. The
  container is specified as an annotation whose value field is an array of the repeatable annotation type. Hence, to
  create a repeatable annotation, firstly the container annotation is created, and then the annotation type is specified
  as an argument to the @Repeatable annotation.

## Predefined/ Standard Annotations

Java popularly defines seven built-in annotations.

- Four are imported from java.lang.annotation: @Retention, @Documented, @Target, and @Inherited.
- Three are included in java.lang: @Deprecated, @Override and @SuppressWarnings
- @Deprecated - It is a marker annotation. It indicates that a declaration is obsolete and has been replaced by a newer
  form.
- @Override - It is a marker annotation that can be used only on methods. A method annotated with @Override must
  override a method from a superclass. If it doesn’t, a compile-time error will result (see this for example). It is
  used to ensure that a superclass method is actually overridden, and not simply overloaded.
- @SuppressWarnings - It is used to inform the compiler to suppress specified compiler warnings. The warnings to
  suppress are specified by name, in string form. This type of annotation can be applied to any type of declaration.
  Java groups warnings under two categories. They are deprecated and unchecked. Any unchecked warning is generated when
  a legacy code interfaces with a code that uses generics.
- @Documented - It is a marker interface that tells a tool that an annotation is to be documented. Annotations are not
  included in ‘Javadoc’ comments. The use of @Documented annotation in the code enables tools like Javadoc to process it
  and include the annotation type information in the generated document.
- @Target - It is designed to be used only as an annotation to another annotation. @Target takes one argument, which
  must be constant from the ElementType enumeration. This argument specifies the type of declarations to which the
  annotation can be applied. The constants are shown below along with the type of declaration to which they correspond.

## User-defined (Custom) - User-defined annotations can be used to annotate program elements, i.e. variables, constructors, methods, etc. These annotations can be applied just before the declaration of an element (constructor, method, classes, etc). 

Do keep these certain points as rules for custom annotations before implementing user-defined annotations.

- AnnotationName is an identifier.
- The parameter should not be associated with method declarations and throws clause should not be used with method
  declaration.
- Parameters will not have a null value but can have a default value. Default value is optional.
- The return type of method should be either primitive, enum, string, class name, or array of primitive, enum, string,
  or class name type.
