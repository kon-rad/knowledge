
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
- almost all functions around networking, use the OS's async features
  - these tasks are done in the 'pendingOSTasks' array in the below event loop
- Threadpool has 4 threads in it
- networking, http module does not work with the thread pool
- fs module, and crypto module does work with thread pool
- file system calls; thread is switched to another while waiting for os to read hard drive
    in this time, takes another task, normally it is fast but if has to switch will take longer

Diagram:
```

const pendingTimers = [];
const pendingOSTasks = [];
const pendingOperations = []; // these are operations that use libuv, like fs, or crypto functions, these use multithreading

function shouldContinue() {
  // check 1: any pending setTimeout, setInterval ...
  // check 2: Any pending OS tasks? like server listening to port
  // check 3: Any pending long running operations? like fs module
  return pendingTimers.length || pendingOSTasks.length || pendingOperations.length;
}

// entire body executes in one 'tick'
while(shouldContinue()) {
  // 1. node looks at pendingTimers and sees if any functions are ready to be called
  // 2. node looks at pendingOSTasks and pendingOperations and calls relevant callbacks
        - run callbacks for any os tasks, or threadpool tasks that are done, (99% of our code)
  // 3. pause execution, continue when...
      // - a new pendingOSTask is done
      // - a new pendingOperation is done
      // - a timer is about to complete
  // 4. look at pendingTimers. call any setImmediate
  // 5. Handle any close events
}

```

## Enahncing Performance
- use Node 'Cluster' mode
- experimental: Use Worker threads
- use ab for benchmarking (apache benchmark on macos and linux)

## Clustering
- e.g.: When a request does work and blocks for 5 seconds, each simultaneus request will also be blocked
- cluster manager, is one overarching parent process, responsible for health of single node processes 
- Cluster manager is not responsible for requests, or database
- clustering start up multiple instances of you server that more evenly address all incoming requests for more predictable response times
- match number of clusters to physical cores on your machine (macbook -> two cores)
- pm2 cli is best cluster management open source software
- `pm2 start index.js -i 0` -i 0 means starts up number of instances equal to logical CPU cores on your computer
- 2 cores x 2 threads = 4 logical cores
- `pm2 list` - `pm2 show` - `pm2 monit`

## Worker threads
- `npm i --save webworker-threads`
