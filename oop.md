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

Containership/Composition (has a):
Using an object within another.
Car **has a** Wheel

Class Relationships(weak to strong):
Using: temporarily use an object
Aggregation: class holds a reference to an object but doesn't control it
Composition: child class owns part of parent class's member objects 
Inheritance (strongest relationship): child class inherits all data members from parent class

The difference between aggregation and composition is that with aggregation, the child can exist independently, whereas in composition, the child cannot exist independent and is tied to the concept of the parent class.
