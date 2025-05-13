# OOP

OOP: Software design organized through objects rather than functions

Classes and Objects:
Class: User defined data type that acts as a blueprint for class instances, which are called objects
Object: Instance of a class with specific data

Methods and Attributes:
Methods: Action that an object can perform
Attributes: Data

Encapsulation:
A class is a unit that has methods and attributes as a part of it. This class exposes specific data using access specifiers.

Abstraction:
Simplified classes over complex implementation code (ie. ignition switch vs engine mechanics). Interfaces and Abstract Classes.
Interface: contract that specifies the implementation of a class that implements it. Use for common behavior.
Abstract: blueprint class that cannot be instantiated but must be inherited. Use for common implementation.

Polymorphism:
Uniform treatment of classes in a class hierarchy. Allows the same code to be used with different objects and behave differently with each.

Inheritance (is a):
With inheritance, classes automatically inhabit the same properties and functionalities as their parent class. This functionality can be modified and/or extended.
Dog **is an** Animal
Dog **extends** Animal

Association (has a):
Unidirectional (ie. Wallet and Money) or Bidirectional (ie. Teacher and Classroom in the case of teacher class knows about their designated classroom and classroom class knows who teaches in the room) reference. Further differentiated into Aggregation and Composition based on the appropriate designation of object ownership.
Example: Teacher -> Student (teacher teaches student)

Object Lifecycle:
Period from object creation to its destruction

Class Relationships(weak to strong):
The way in which class relationships are designed are dependent on the implementation details. Context matters, and more specifically, the scope of concepts (ie. Engine/Tire in a supplier context of a racing game context). In the case of a Car and Engine, if the context were to be parts in an auto shop, the appropriate class relationship between Car and Engine would be aggregation, because the engine is not owned by the car but the car has an engine and this can be swapped out. In the context of a racing game, it would be better for this class relationship to be compositional, because the car owns the engine.

Dependency: class A temporarily uses class B, but neither A nor B strictly own each other (loose coupling). Temporary relationship.
Example: Mechanic uses a Tool

Aggregation (has a, unidirectional relationship, Class A knows Class B but not vice versa, loosely coupled because lifecycles of both objects are independent/do not depend on one another): class holds a reference to an object but doesn't control it. Contained class can still exist independently. 
Example: One-to-one or one-to-many or many-to-many. School has Principal(1-1), School has Student(1-many). Teacher has Student(many-to-many). Child class comes and goes (ie. Passengers in a Car, Students in a Lecture, Weapons in a Player, Books in a Library). Directionality and Cardinality are different. While the cardinality can be many-to-many, an aggregation relationship is unidirectional.

Composition (class B is part of class A/class A consists of class B, or strong has a, tightly coupled because dependent lifecycles): child class owns part of parent's class's member objects  
Example: One-to-one or one-to-many. House has rooms(1-many). Car has engine(1-1). Child class gets destroyed when the parent gets destroyed. There cannot be many-to-many relationships in a compositional relationship because class A has exclusive ownership of its children. 

Inheritance (is a): child class inherits all public/protected data members and methods from parent class, doesn't inherit constructors
Example: Dog is an Animal

The difference between aggregation and composition is that with aggregation, the child can exist independently, whereas in composition, the child cannot exist independently and is tied to the concept of the parent class.

![image](https://github.com/user-attachments/assets/fa493c6c-0440-41cb-9f51-8360aaf67541)
Source: https://www.geeksforgeeks.org/association-composition-aggregation-java/

![image](https://github.com/user-attachments/assets/98e11fab-7e1c-4eaa-a825-e0285a169ab8)
Source: https://www.umlboard.com/docs/relations/

