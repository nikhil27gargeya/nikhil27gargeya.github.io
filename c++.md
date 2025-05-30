# C++

LearnCPP

When a program (sequence of instructions for performing a task) runs, it takes up memory. Everytime a variable is created the program allocated more memory to store it 

General Memory Layout:
stack: stores local variables
heap: dynamic memory for programmer to allocate
data: for global variables
text: stores the code being executed

Stack memory allocatino is automatically done

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
