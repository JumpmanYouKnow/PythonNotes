---
title: "Difference between Multi-Processing, Multi-threading and Coroutine"
date: 2019-04-08
---
How is a computer program executed? A program needs at least one **thread**, one **process**, one **core**, one **CPU** to run on.
A thread lives in process, a process lives in core, a core lives in a CPU.
-  In a same CPU, there can be multiple cores. Different cores work together and share resources.
Across different CPUs there could be also multiple cores, but usually not a good practice, for same amount of cores, we usually have a lot better performance gain by putting them in a same CPU. Now for commercial CPU, 16 cores is pretty common.
Before we go any deeper, we must be clear of two concept:
## Concurrent and Parallel
Concurrent: When
Parallel: Execution at the same time.
## What is a process 
### For distributing
## What is a thread
### Advantage
## What is a Coroutine
### Why we prefer coroutine in Python
### Tornado, Greenlet, Gevent
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAyNjMxMDczNSwtMTIyNjYwMTgzMywtNj
AxMTM1MjkwLDE5NzgxODgzMTQsNTg0MTYwNjBdfQ==
-->