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
Simpliifed classes over complex implementation code (ie. ignition switch vs engine mechanics)

Inheritance (is a):
With inheritance, classes automatically inhabit the same properties and functionalities as their parent class. This functionality can be modified and/or extended.
Dog **is an** Animal
Dog **extends** Animal

Polymorphism:
Uniform treatment of classes in a class hierarchy. Allows the same code to be used with different objects and behave differently with each.

Association (has a):
There are different strengths of associative relationships which are described below:
Using an object within another.
Car **has a** Wheel

Object Lifecycle:
Period from object creation to its destruction

Class Relationships(weak to strong):
Dependency: class A temporarily uses class B, but neither A or B strictly own each other. Temporary relationship.
Example: Car and Engine. Engine lifecycle exists insofar as the car is driven. Car is dependent on the ngine to drive, and this is a temporary relatinoship.

Aggregation (has a): class holds a reference to an object but doesn't control it. Contained class can still exist independently. 
Example: Driver has a car. Car can exist independently of the driver. Child class comes and goes (ie. Passengers in a Car)

Composition (part of, or strong has a): child class owns part of parent class's member objects  
Example: Wheel is part of a Car. The Car owns its wheels. Child class gets destroyed when the parent gets destroyed.

Inheritance (is a): child class inherits all public/protected data members and methods from parent class, doesn't inherit constructors
Example: 

The difference between aggregation and composition is that with aggregation, the child can exist independently, whereas in composition, the child cannot exist independently and is tied to the concept of the parent class.
