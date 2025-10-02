A data structure in most OSs that holds all information needed to manage a process throughout its entire lifecycle.

The OS makes sure each [[process]] has a process control block. 

The process control block (PCB) holds the 
[[process id]] (PID), 
[[parent process id]] PPID,
[[process state]], 
[[program counter]],
[[stack pointer]] 
CPU registers values, 
Segment register values,
pointer to [[page table]]
[[pages]], 
memory allocation details, 
I/O information, 
Open Files - Descriptor 

The advantages of PCB include:
[[context switch]] to different processes efficiently
manage system resources for each process
schedule a process for the CPU execution
Track and control process thorughout its execution

PCBs are stored in protected memory so user level processes cannot access them.
Frequently accessed PCB information may be stored in the [[cache]] in CPU registers or fast memory

When a process terminates, the OS cleans up the PCB
