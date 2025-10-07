best when tasks share data, need concurrency and dont require isolation

[[synchronization]] - threads moving independently but together moving towards a single goal 

Processes are more expensive than threads.

threads running from the same [[process]] have a different execution context
threads share the same code, heap, static data, code, file descriptors
- reduces OS overhead

Apps like web browsers need concurrent tasks to handle multiple incoming requests, creating a lot of tasks. Threads can be created to handle these tasks.

Context switching in threads are different than processes. Threads only need to save registers and restore registers of new thread.

process have better isolation making it hard to corrupt each other.

threads sacrifice isolation for speed
- can overwrite each other thread's data

kernel is not needed for context switching in user level threads

creating threads can cause a lot of overhead
Thread pools - create existing threads ahead of time to handle multiple requests. some of these threads can be idle
pool size is constrained by available resources

Example: A web server hands each client connection to each thread which serves the same serevr. Incoming requests take an idle thread; if none are free, they queue. After work completes, the thread returns to the pool.

4 threads are running at the same time in a 4 core cpu. 

threads enable parrelelism and different cores run different threads of the same process simultaneously. 
thread affinity can pin threads to a core.

user level threads live in user space in a thread library uses the process time slice

any blocking system call by one thread blocks the whole process since the kernel cant distinguish between them

Kernel level threads move the thread table and scheduling into the OS

Kernel level threads are modern and scheduled using the kernel. When a kernel level thread blocks, the kernel can run another thread from the same process, or a thread from a different process giving it a huge advantage over user level thread, but creates overhead.

each kernel thread gets its own time slice, so multi-threaded programs scale their CPU share with thread count

Kernel level thread context switch can be as slow as process context switch and increases overhead







