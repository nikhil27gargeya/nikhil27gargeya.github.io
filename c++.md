# C++

LearnCPP

When a program (sequence of instructions for performing a task) runs, it takes up memory. Everytime a variable is created the program allocated more memory to store it 

General Memory Layout:
stack: stores local variables
heap: dynamic memory for programmer to allocate
data: for global variables
text: stores the code being executed

Stack memory allocation is automatically done

When a function returns, the stack memory gets dealocated, so it ain't good to return a pointer in a helper function

Programs are executed on hardware:
CPU: executes instructions, the brain of the computer
Memory: where programs are loaded prior to execution
I/O: input and output devices
Storage: where data is stored

Platform: an environment for software which includes compatible set of hardware and software

CPUs can only understand machine language

Assembly language: human readable machine language. It is translated to machine code through the use of an assembler.

Low level language: called low level because there is minimal abstraction. A low level language is tailored to a specific instruction set architecture.

2 ways of translating a high level language to machine code:
-compiling
-interpreting

Compiler reads the source code and translates it to a low level language (ie. machine code). The resulting machine code can be packaged into an executable file. Compilers were not always good but now they produce fast machine code. High level code -> compiler -> machine code -> executable -> hardware -> result

Interpreter: directly executes instructions in the source code without compiling. They are more flexible but slower. High level code -> interpreter -> hardware -> result

--

Before C++, C was created for creating OS, it was designed to produce efficient code, exercise memory control, and be portable so that UNIX(an operating system) could be recompiled on different computers.

Bjourne Stroustrup created C++ at Bell Labs (in 1979), the most notable innovation over C is the introduction of OOP.
5 majors updates were C++11, 14, 17, 20, 23. C++11 is widely considered the baseline language.
C++ is good at:
video games
high performance financial applications
graphical applications
embedded systems
AI

--

Compiling source code steps:
the compiler sequentially goes through each cpp file and checks for syntax errors. Then it translates the code to machine code with object files being used as an intermediate step which includes data needed for the linker. Then the linker combines all the object files as well as libraries and produces the executable file.

C++ standard library contains iostream which provides the functionality for displaying text and receiving input from the user.

An IDE (integrated development environment) is a piece of software that makes it easy to develop, build, and test software.

A build target is a collection of project settings that determines how the IDE will build the project.

--
Every c++ program must have a special function called main, without main the program will fail to link

The name of a function is called an identifier

#include <iostream> //example of a preprocessor directive, tells the compiler we want the iostream library 

--
Data: information that can be moved, processed or stored by a computer
in C++, direct memory access is discouraged, instead we access memory through the use of objects
An object is a region of storage (typically RAM or a CPU register)

int x;
at compile time, the compiler makes a note that we want a variable that is of the type int.
compile time means when the program is checked for syntax and type errors
runtime means when the program is loaded into memory and executed
