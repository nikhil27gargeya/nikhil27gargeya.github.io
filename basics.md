# Basics:

Language: tool to write code
Library: prewritten codebase that is a piece in the build
Framework: Blueprint on which your code functions on

Software exists within a framework
Software contains libraries

Code calls a library vs. Framework calls code

Strongly vs Weakly Typed:
Strongly Typed: type rules are enforced by the compiler. Error will be thrown if there are operations between incompatible types. Explicit conversions are required in most cases. (ie. python, java, c(has some implicit conversion, like int -> long bc no loss in precision), swift(has no implicit conversion))
Weakly Typed: type rules are not enforced by the compiler. Implicit/type conversions. (ie. javascript, php)

Statically vs Dynamically Typed:
Statically Typed: type rules are enforced at compile time, the compiler type checks at runtime (ie. java, c, swift)
Dynamically Typed: type rules are enforced at run time (ie. javascript, python)

Pros of Swift:
Type Inference
Strongly typing (type safe)
Optionals
ARC Memory management

Cons:
Documentation changes rapidly(ie. Migrating from the Observable Object protocol to the Observable macro)
Tied to Xcode

Shallow copy vs Deep copy:
Shallow copy: a new object with references to the original object's data, changes affect the original
Deep copy: a new object with independent copies, changes don't affect the original

Pointer vs Reference
Pointer: stores a memory address, it points to the location of data in memory
A pointer is a primitive data type just like an integer and character.

Primitive data type:
basic data types built into a language (ie. int, char, float, void), stored on the stack

Non-Primitive data type:
built from primitive types or built by programmer (arrays, linked lists, stacks, queues, etc.) and these objects stored on the heap (their reference variables still exist on the stack)

Size of data types:
Integer: 4 bytes
Character: 1 byte
Pointer: 4 bytes on 32 bit machine, 8 bytes on 64 bit machine


Reference: an alias variable 

