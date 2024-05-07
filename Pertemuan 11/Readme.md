4.1 Provide three programming examples in which multithreading provides
better performance than a single-threaded solution.
Answer:
a. A Web server that services each request in a separate thread.
b. A parallelized application such as matrix multiplication where
different parts of the matrix may be worked on in parallel.
c. An interactive GUI program such as a debugger where a thread is
used to monitor user input, another thread represents the running
application, and a third thread monitors performance.

4.2 What are two differences between user-level threads and kernel-level
threads? Under what circumstances is one type better than the other?
Answer:
a. User-level threads are unknown by the kernel, whereas the kernel
is aware of kernel threads.
b. On systems using either M:1 or M:N mapping, user threads are
scheduled by the thread library and the kernel schedules kernel
threads.
c. Kernel threads need not be associated with a process whereas every
user thread belongs to a process. Kernel threads are generally
more expensive to maintain than user threads as they must be
represented with a kernel data structure.

4.3 Describe the actions taken by a kernel to context-switch between kernellevel threads.
Answer:
Context switching between kernel threads typically requires saving the
value of the CPU registers from the thread being switched out and
restoring the CPU registers of the new thread being scheduled.
