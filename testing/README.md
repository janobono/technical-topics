# Testing

## TDD

Test Driven Development (TDD) is software development approach in which test cases are developed to specify and validate
what the code will do. In simple terms, test cases for each functionality are created and tested first and if the test
fails then the new code is written in order to pass the test and making code simple and bug-free.

Test-Driven Development starts with designing and developing tests for every small functionality of an application. TDD
framework instructs developers to write new code only if an automated test has failed. This avoids duplication of code.
The TDD full form is Test-driven development.

Test-Driven development is a process of developing and running automated test before actual development of the
application. Hence, TDD sometimes also called as Test First Development.

## BDD

Behavior Driven Development (BDD) is a branch of Test Driven Development (TDD). BDD uses human-readable descriptions of
software user requirements as the basis for software tests. Like Domain Driven Design (DDD), an early step in BDD is the
definition of a shared vocabulary between stakeholders, domain experts, and engineers. This process involves the
definition of entities, events, and outputs that the users care about, and giving them names that everybody can agree
on.

BDD practitioners then use that vocabulary to create a domain specific language they can use to encode system tests such
as User Acceptance Tests (UAT).

Each test is based on a user story written in the formally specified ubiquitous language based on English. (A ubiquitous
language is a vocabulary shared by all stakeholders.)

## unit tests

Unit tests are very low level, close to the source of your application. They consist in testing individual methods and
functions of the classes, components or modules used by your software. Unit tests are in general quite cheap to automate
and can be run very quickly by a continuous integration server.

## integration tests

Integration tests verify that different modules or services used by your application work well together. For example, it
can be testing the interaction with the database or making sure that microservices work together as expected. These
types of tests are more expensive to run as they require multiple parts of the application to be up and running.

## functional tests

Functional tests focus on the business requirements of an application. They only verify the output of an action and do
not check the intermediate states of the system when performing that action.

There is sometimes a confusion between integration tests and functional tests as they both require multiple components
to interact with each other. The difference is that an integration test may simply verify that you can query the
database while a functional test would expect to get a specific value from the database as defined by the product
requirements.

## mocks

Mocking means creating a fake version of an external or internal service that can stand in for the real one, helping
your tests run more quickly and more reliably. When your implementation interacts with an object’s properties, rather
than its function or behavior, a mock can be used.

## stubs

Stubbing, like mocking, means creating a stand-in, but a stub only mocks the behavior, but not the entire object. This
is used when your implementation only interacts with a certain behavior of the object.

## spies

Spies are known as partially mock objects. It means spy creates a partial object or a half dummy of the real object by
stubbing or spying the real ones. In spying, the real object remains unchanged, and we just spy some specific methods of
it. In other words, we take the existing (real) object and replace or spy only some of its methods.

Spies are useful when we have a huge class full of methods, and we want to mock certain methods. In this scenario, we
should prefer using spies rather than mocks and stubs. It calls the real method behavior, if the methods are not
stubbed.

## JUnit

JUnit is a unit testing framework for Java programming language. JUnit has been important in the development of
test-driven development, and is one of a family of unit testing frameworks collectively known as xUnit, that originated
with JUnit.

## Mockito

Mockito is a popular open source framework for mocking objects in software test. Using Mockito greatly simplifies the
development of tests for classes with external dependencies.

## PowerMockito

PowerMock is an open-source Java framework used for creating a mock object in unit testing. It extends other mocking
frameworks such as EasyMock and Mockito to enhance the capabilities. The PowerMock framework uses a custom classloader
and bytecode manipulation techniques to enable the mocking of static methods, final classes, final methods, private
methods, constructor, and removal of static initializers. The main aim of PowerMock is to extend the existing APIs with
some methods and annotations to provide extra features that make unit testing quite easy.

The PowerMock framework provides a class called PowerMockito used to create mock objects and initiates verification and
expectation. The PowerMockito provides the functionality to work with the Java reflection API.
