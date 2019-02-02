
# NodeJS

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
- node event loop is single threaded, some of node framework/std libraries are NOT single threaded

## Event Loop
- control structure of what the one thread should be doing in node

Diagram:
```

const pendingTimers = [];
const pendingOSTasks = [];
const pendingOperations = [];

function shouldContinue() {
  // check 1: any pending setTimeout, setInterval ...
  // check 2: Any pending OS tasks? like server listening to port
  // check 3: Any pending long running operations? like fs module
  return pendingTimers.length || pendingOSTasks.length || pendingOperations.length;
}

// entire body executes in one 'tick'
while(shouldContinue()) {
  // 1. node looks at pendingTimers and sees if any functions are ready to be called
  // 2. node looks at pendingOSTasks and pendingOperations adn calls relevant callbacks
  // 3. pause execution, continue when...
      // - a new pendingOSTask is done
      // - a new pendingOperation is done
      // - a timer is about to complete
  // 4. look at pendingTimers. call any setImmediate
  // 5. Handle any close events
}

```


