# Java 11 features

Oracle has revamped its support model and come up with a release train that’ll bring rapid updates, about every 6
months.

Java 11 is the second LTS release after Java 8. Since Java 11, Oracle JDK would no longer be free for commercial use.

Some of the important Java 11 features are:

- Nashorn JavaScript script engine and APIs are deprecated thereby indicating that they will be removed in the
  subsequent releases.
- Remove the Java EE and CORBA Modules, Following packages are removed: java.xml.ws, java.xml.bind, java.activation,
  java.xml.ws.annotation, java.corba, java.transaction, java.se.ee, jdk.xml.ws, jdk.xml.bind
- Flight Recorder which earlier used to be a commercial add-on in Oracle JDK is now open-sourced since Oracle JDK is
  itself not free anymore. JFR is a profiling tool used to gather diagnostics and profiling data from a running Java
  application. Its performance overhead is negligible and that’s usually below 1%. Hence it can be used in production
  applications.

## Running Java File with single command

One major change is that you don’t need to compile the java source file with javac tool first. You can directly run the
file with java command and it implicitly compiles. This feature comes under JEP 330.

## New utility methods in String class

- isBlank() - This instance method returns a boolean value. Empty Strings and Strings with only white spaces are treated
  as blank.
- lines() - This method returns a stream of strings, which is a collection of all substrings split by lines.
- strip() – Removes the white space from both, beginning and the end of string.strip() is “Unicode-aware” evolution of
  trim(). When trim() was introduced, Unicode wasn’t evolved. Now, the new strip() removes all kinds of whitespaces
  leading and trailing(check the method Character.isWhitespace(c) to know if a unicode is whitespace or not)
- repeat(int) - The repeat method simply repeats the string that many numbers of times as mentioned in the method in the
  form of an int.

## Local-Variable Syntax for Lambda Parameters

JEP 323, Local-Variable Syntax for Lambda Parameters is the only language feature release in Java 11. JEP 323 allows var
to be used to declare the formal parameters of an implicitly typed lambda expression. But why is this needed when we can
just skip the type in the lambda? If you need to apply an annotation just as @Nullable, you cannot do that without
defining the type. Limitation of this feature - You must specify the type var on all parameters or none.

## JEP 321: HTTP Client

Java 11 standardizes the Http CLient API. The new API supports both HTTP/1.1 and HTTP/2. It is designed to improve the
overall performance of sending requests by a client and receiving responses from the server. It also natively supports
WebSockets.

## Reading/Writing Strings to and from the Files

Java 11 strives to make reading and writing of String convenient. It has introduced the following methods for reading
and writing to/from the files:

- readString()
- writeString()
