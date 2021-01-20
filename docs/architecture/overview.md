## Concepts
Architecture and design are closely related; the main difference between them is really about which way we face. Architecture faces towards strategy, structure and purpose, towards the abstract. Design faces towards implementation and practice, towards the concrete.

- Architecture - A plan for the structure of something.
- Design - A plan to create something.

[https://simplicable.com/new/architecture-vs-design]()

### Architectures
- Monolith
- Microservice

While a monolithic application is a single unified unit, a microservices architecture breaks it down into a collection of smaller independent units. These units carry out every application process as a separate service. So all the services have their own logic and database as well as perform specific functions.
### Design Patterns
- Adapter: helps two incompatible interfaces to work together.
- Builder: create complex objects that are hard to configure.
- Command: performs some specific task without having any information about the receiver of the request.
- Composite: builds a hierarchy of tree objects and interacts with all of them the same way.
- Decorator: vary the responsibilities of an object adding some features.
- Factory: create objects without having to specify the exact class of the object that will be created.
- Interpreter: provides a specialized language to solve a well defined problem of a known domain.
- Iterator: provides a way to access a collection of sub-objects without exposing the underlaying representation.
- Observer: helps building a highly integrated system, maintainable and avoids coupling between classes.
- Proxy: allows having more control over how and when access is permitted to a certain object.
- Singleton: have a single instance of certain class across the application.
- Strategy: varies part of an algorithm at runtime.
- Template Method: redefines certain steps of an algorithm without changing the algorithm's structure.

## Paradigms
a way to classify programming languages based on their features.

[https://en.wikipedia.org/wiki/Comparison_of_programming_paradigms]()

### Functional
Treats computation as the evaluation of mathematical functions avoiding state and mutable data.
### Object Oriented
Treats datafields as objects manipulated through predefined methods only.

## Type Systems
### Statically/Strongly Typed
Once you set a variable to a type, you cannot change it.
### Dynamically Typed
Do type checking at run-time as opposed to compile-time.

## Recursion
A recursive method solves a problem where the solution depends on solutions to smaller instances of the same problem. (The definition contains a call to itself.)

## Object Orientation
#### Encapsulation
is a process of wrapping code and data together into a single unit.
#### Abstraction
is a technique for arranging complexity of computer systems. It works by establishing a level of complexity on which a person interacts with the system, suppressing the most complex details below the current level
#### Inheritance
is when a class inherits behavior from another class. The class that is inheriting behavior is called the subclass and the class it inherits from is called the superclass.
#### Polymorphism
is a method where one is able to execute the same method using different objects.

## SOLID Principles
Helps developers design flexible solutions, detect code smells, and refactor their code to prevent issues. By following SOLID design principles, developers can achieve a maintainable and extendable codebase.

A class should only have a single responsibility, that is, only changes to one part of the software's specification should be able to affect the specification of the class.
#### Single Responsibility Principle
A class should have a single responsibility. The goal of the SRP principle is to fight complexity that creeps in while you’re developing an application’s logic.

Software entities should be open for extension, but closed for modification.

A module should be responsible to one, and only one, actor.
#### Open-closed Principle
Modules, classes, methods and other application entities should be open for extension but closed for modification. Modules, classes, methods, etc. should be designed in a modular way so that you are able to change the behavior of the system without changing the source code. helps developers achieve a flexible system architecture.

Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program.

A software artifact should be open for extension but closed for modification.
#### Liskov Substitution Principle
Subclasses should add to a base class’ behaviour, not replace it. parent instances should be replaceable with one of their child instances without creating any unexpected or incorrect behaviour. LSP ensures that abstractions are correct, and helps developers achieve more reusable code and better organize class hierarchies.
#### Interface Segregation Principle
Clients shouldn’t depend on methods they don’t use. Several client-specific interfaces are better than one generalized interface. Main classes should be segregated into smaller specific classes, so their clients use only methods they need. As a result, we get the interfaces segregated according to their purpose, so we avoid “fat” classes and code that’s hard to maintain.

Many client-specific interfaces are better than one general-purpose interface.
#### Dependancy Inversion Principle
High-level modules shouldn’t depend on low-level modules. Both modules should depend on abstractions. In addition, abstractions shouldn’t depend on details. Details depend on abstractions.

One should depend upon abstractions, not concretions.

## DRY Principle
"Don't Repeat Yourself."

is stated as "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system". ... When the DRY principle is applied successfully, a modification of any single element of a system does not require a change in other logically unrelated elements.

## Software Development Life Cycle (SDLC)
is a process used by the software industry to design, develop and test high quality softwares. The SDLC aims to produce a high-quality software that meets or exceeds customer expectations, reaches completion within times and cost estimates.

## TODO
- Mutation v Replacement