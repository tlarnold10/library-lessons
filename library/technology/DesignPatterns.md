# Design Patterns: Elements of Reusable Object-Oriented Software
__By: Erich Gamma__
## Lessons Learned:
- A pattern has 4 essential elements:
    1. Pattern name
    2. The problem describes when to apply the pattern
    3. The solution describes the elements that make up the design, their relationships, responsibilities, and collaborations.
    4. The consequences are the results and trade-offs. Often around concerns of space and time trade offs. 
- Design patterns are descriptions of communicating objects and classes that are customized to solve a general design problem in a particular context.
- We classify design patterns by two criteria
    1. Purpose (what does the pattern do)
        - Creational patterns concern the process of object creation
            1. Factory Method
                - for GUIs in the situation that they have to work on multiple platforms. Initialize guiFactory at a point in the program before it's ever used to create widgets but after it's clear which look and feel is desired
            2. Abstract Factory
            3. Builder
            4. Prototype
            5. Singleton
                - Use when there must be exactly one instance of a class
        - Structural patterns deal with the composition of classes or objects
            1. Adapter (class)
                - Use when you want to use an existing class, but its interface does not match the one you need
            2. Adapter (object)
            3. Bridge
            4. Composite
            5. Decorator
            6. Facade
            7. Flyweight
            8. Proxy
        - Behavioral patterns is the way classes or objects interact and distribute responsibility. 
            1. Interpreter
            2. Template Method
            3. Chain of Responsibility
            4. Command
            5. Iterator
            6. Mediator
                - A mediator is responsible for controlling and coordinating the interactions of a group of objects. The mediator serves as an intermediary that keeps objects in the group from referring to each other explicitly. The objects only know the mediator, thereby reducing the number of interconnections. 
            7. Memento
                - A memento is an object that stores a snapshot of the internal state of another object - the memento's originator. 
            8. Observer
            9. State
            10. Strategy
            11. Visitor
    2. Scope (pattern applies to classes or objects)
        - Objects - changed at run time
        - Most patterns are object scooped
- Design patterns help determine what objects should be created and what the size of those objects should/can be
- The set of all signatures (an operation's name, the parameters, and return value) defined by an objects operations is called the interface to the object
    - Objects are known only through their interfaces
- Dynamic binding lets you substitute objects that have identical interfaces for each other at run time. This substitutability is known as polymorphism. 
- Classes that are not abstract are called concrete classes
- Class vs. type
    - An object's class defines how the object is implemented (internal state and the implementation of its operations). An object's type only refers to its interface - the set of requests of which it can respond
    - An object can have many types, and objects of different classes can have the same type
- Object composition is an alternative to class inheritance. Here, new functionality is obtained by assembling or composing objects to get more complex functionality 
    - Black-box reuse
    - Inheritance uses white-box
    - It is said that inheritance breaks encapsulation because the sub-class is so tied to the parent class. This is why you might want to use something like object composition. 
- Composition is a concept in object-oriented programming that models the relationship between two classes. Composition involves using other classes to build more complex classes and there is no parent/child relationship exists in this case. Basically, complex objects are composed of other objects. Composition represents a has-a relationship. For example, consider the computer as an object. Computer has-a motherboard, keyboard, speaker, etc. Composed objects also can be composed of other objects. For example, motherboard has-a RAM, CPU, etc. Like Inheritance, composition is a mechanism for reuse. You could remove some parts and install them in other computers.
- Parameterized types
    - example: List<String>
    - Also known as generics or templates
    - Lets you define a type without specifying all the other types it uses. The unspecified types are supplied as parameters at the point of use
- Aggregation implies that one object owns or is responsible for another object. Acquaintance implies that an object merely knows of another object. 
    - Aggregation and acquaintance are difficult to tell apart because they are often implemented the same way. 
- Design patterns are helpful in creating software that can easily change. Different design patterns address different kinds of change.
- Frameworks emphasis design reuse over code reuse
- Frameworks vs design patterns
    1. Design patterns are more abstract
    2. Design patterns are smaller architectural elements than frameworks. A framework contains several design patterns but the reverse is never true
    3. Design patterns are less specialized than frameworks
- Recursive composition - building increasingly complex elements out of simplier ones
    - Think several components of a car all coming together
- Three  object-oriented software phases: prototyping, expansionary, and consolidating
- The continual need to satisfy more requirements along with the need for more reuse propels object-oriented software through repeated phases of expansion and consolidation - expansion as new requirements are satisfied, and consolidation as the software becomes more general. 