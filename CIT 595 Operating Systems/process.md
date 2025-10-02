Processes are instances of a [[program]] loaded into memory and is running. The OS manages and controls all aspects of processes. Each process is unique even if it comes from the same [[program]]. Each process has its own [[virtual memory]] as well as CPU time, files, and many other resources.

The OS also has a PCB, [[process control block]] for each process to track its different [[process states]] as well as many other components to save details of a process when it transitions between each of the [[process states]].

Each process can have a [[child process]] which is created through the fork() operation. 

the OS maintains the [[context switch]] of each process

A process's content includes its the data in virtual memory, CPU registers,  process state, process id, and open files which are all stored into the [[process control block]] during a [[context switch]]

Processes usually always start off at the ready state

init process -> starts the daemon process 
Orphan process = no parents
zombie process = parent does not call wait on the child before it terminates so we lose a pid.

processes can be in a process group. If a signal is sent to a process group, every process will receive that signal

The child process of a parent have the same PGID to the parent
SET PGID to set the childs to a different pgid