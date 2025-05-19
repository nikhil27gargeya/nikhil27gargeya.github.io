# OS

Operating System: A body of software allowing programs to run and share memory with each other, sometimes called a resource manager
Topics:
1. Virtualization
2. Concurrency
4. Persistence

What happens when a program runs:
processor decodes fetches instructions, decodes them, and executes it

What is a physical resource:
processor, memory/RAM, disk

The OS takes these physical resources and virtualizes them





Difference between 32 bit and 64 bit architecture:
32 bit: 
Memory Limit: can access maximum 2^32 different memory addresses = 4 GB of RAM (actual access amount is around 3.5 GB because part of the register stores temporary values)
Handling Limit: handles 32 bits of data at a time
64 bit: 
Memory Limit: can access maximum 2^64 different memory addresses = more than 4GB of Ram (to be precise 16 exabytes)
Handling Limit: handles 64 bits of data at a time

More cores of a processor means more calculations per second that can be performed -> faster compute

32 bit architecture uses 4 bytes for a pointer while 64 bit architecture uses 8 bytes for a pointer. Moving less data around in the case of 32 bit architecture could be less intensive which could be an advantage.

x64: 64 bit architecture
x86: 32 bit architecture
