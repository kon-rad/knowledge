
# NodeJS

## Event Loop
- control structure of what the one thread should be doing in node


## Threads
- OS scheduling, is your computers ability to decide when to perform which process
- To process more threads at a time, add more CPU cores or ...
  - I/O input or output operations takes time, for example reading files off a hard drive
  - During that time CPU is waiting on hard drive to read file, OS scheduler can 
      detect this pause between instructions and can decide to pause thread #1 and 
      execute another thread, 
- Threads are units of instructions waiting to be executed by the CPU
- deciding which order to execute the threads in is referred to as scheduling, which is controlled by the OS
- to incrase rate of processing threads either 1. increase number of cpus 2. detect pauses during I/O operations

