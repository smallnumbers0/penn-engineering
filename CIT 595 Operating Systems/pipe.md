
using the "|" we can run multple processes concurrently

**Concurrent execution**: Pipeline stages like p1 | p2 | p3 run at the same time. The sleep 10 | sleep 100 example finishes in **100 seconds**, proving parallelism; you block until the slowest completes.

Even though stages run concurrently, throughput is limited by the slowest stage.

Children inherit all pipe fd(s). Use dup2 to map the correct ends to stdin/stdout, then close unused ends to avoid hangs.

Children of a command line are grouped under a **PGID** (typically the first child’s process id).

dup2 is used to redirect stdout of p1 to be the write end of pipe
dup2 is used to redirect stdin of p2 to be the read end of pipe

There can be temporary zombies. We should call wait pid.

the output of a [[process]] becomes the input of the next [[process]] in the pipeline

half duplex means data flows in one direction only

fd[0] for reading
fd[1] for writing

output of fd[1] always goes to fd[0]

pipe is a finite buffer where p1 and p2 runs concurrently

if we don't close ends of pipes we end up in a [[deadlock]]

**Closing pipe ends**: Failing to close the **write end** can prevent EOF and cause blocking. Leaving the read end open usually doesn’t block, but good hygiene is to close both unused ends, including in the parent.

ls | grep "pdf" 

output of ls goes to 

synchronization

synchronous - busy wait on all child processes by having a loop on each child which blocks
asynchronous - signals that parents wait for to see if the child has exited. sigchld signal is sent to SIGCHLD sig handler this is non blocking

**Semantics of separators**: Pipelines (|) run commands concurrently and stream data; semicolons (;) run commands **sequentially**. Hence sleep 2 | sleep 3 takes **3 seconds**; sleep 2 ; sleep 3 takes **5 seconds**.