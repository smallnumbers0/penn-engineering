Sometimes we may have 20 processes to run on 4 cores, so processes toggle between running and ready state.
the cpu [[scheduler]] choses which process to run:

Different types of states include:

Ready - eligible to be selected to run. 
Running - process is running
Blocked - waiting for something like a [[system call]]

when a process is unblocked usually signaled by a [[hardware interrupt]], it is put in a ready state, and does not run immediately

examples of going to block state include writing to disk because writing to disk is very slow

non-preemptive - running until allocated time slice with no forced interruption

preemptive - running state to ready after going through a time slice or until interrupted

Blocking wait() 

after a fork() parent calls wait(&status) on child and the parent is blocked. After the child exit(), the parent is unblocked and put in ready state

