---
title: "Difference between Multi-Processing, Multi-threading and Coroutine"
date: 2019-04-09
---
How is a computer program executed? A program needs at least one thread to run on.
And  a **coroutine** live in a thread, a **thread** lives in process, a **process** lives in core, a **core** lives in a CPU.

- Multi-Processing usually refer to many processes execute in **parallel**. Process is smallest resource management unit, different process share different resource.
- Multi-Threading usually refer to many threads execute **concurrently**, when there are idle cores, threads can use idle cores to run in **parallel**. Thread is smallest execution unit, a program needs at least one thread to run.
- Coroutine usually refer to many routines execute **concurrently**.

## Concurrent and Parallel
Many threads live in a process, only one thread can own the process, when they own the process, they can run, they take turns to own the core.

**Concurrent**: Thread A and Thread B are in same process, takes turns to own the process,  yield when waiting for resources or scheduled cpu time is used up.
Use case is dealing with I/O-intensive tasks.
**Parallel**: Thread A and Thread B are in different processes, execute at the same.
Use case is dealing with CPU(Data)-intensive tasks.

## CPU(Data) intensive tasks
Usually use multi-processing and multi-threading, as a normal task won't wait for some external data, it needs cpu to do computation for most of the time.
But which one to choose is depend on different kinds of computing tasks.
### Multi-threading vs Multi-processing
Thread is lighter than process, lighter means easy to create and destroy, occupy less resource.
Threads share same address space, heap but each thread has its own stack.
- Communication between threads is faster.
- Multi-processing is more reliable, one process is crashed -> won't affect other processes. On contrast, one thread crashes, the process it belongs to, as well as other threads in the same process become dead.

Overall, multi-threading is good for co-operative tasks, multi-processing is good for isolated tasks.
For example, if the tasks are highly related and need frequently create/destroy sub-tasks, (like running O(n) parallel BFS algorithm ), multi-threading is preferred.
Otherwise, tasks like running a multi-processing(computing page-rank from 3 different sources in parallel) is preferred.

Example: Spark, Hadoop, distributed computing.


## I/O-intensive tasks
Usually use multi-threading and coroutine, as a normal task spends most of its time waiting for I/O(Disk, Network, RAM).

Example: Web servers, Tornado, Gevent

### Coroutine vs Multi-threading
Coroutine is one of the reason why Python, Go are so popular to write web servers.
Coroutines run concurrently in a thread just like threads run concurrently in a process. 
But:
 - Concurrent execution needs context-switch and context-switch by coroutine is extremely light, which means much cheaper, faster than multi-threading
 - Coroutine is managed by user,  multi-threading is managed by kernel. Developers have better control of the execution flow by using coroutine, for example, a coroutine won't be forced to yield.
 - Coroutines cannot run in parallel.
 
### I/O intensive in Python
In python, because of the existence of GIL(one GIL per process),  so only one thread can acquire the GIL to run at the same time even, so multi-threading isn't really multi-threading in python, as threads can only run concurrently but not in parallel. 
So coroutine and multi-threading has no difference except multi-threading is heavier and slower in Python.

In python, we use multi-processing lib for CPU-intensive tasks. Multi-processing lib allows each process have its own GIL.
###  I/O intensive in Python
Use coroutine lib like asyncio, gevent, or framework like Tornado for I/O-intensive tasks.

###  CPU intensive in Python
Use multi-processing

### Need some sort of combination? 
Use coroutine and reimplement key module using C to avoid GIL.
 
## Multi-core CPU vs Multi-CPU
-  In a same CPU, there can be multiple cores. Different cores work together and share resources.
Across different CPUs there could be also multiple cores, but usually not a good practice because some resources are not shared, getting resources owned by other CPU is expansive.
For same amount of cores, we usually have a lot better performance gain by putting them in a same CPU. Now for commercial CPU, 16 cores is pretty common. Multi-CPU is usually good for running completely isolated programs (not sharing any data)
