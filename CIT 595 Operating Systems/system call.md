All system calls run code in the [[kernel]]. This system call function code lives in the OS. 
Uses a different [[virtual memory]] so [[context switch]] is required

## Invoking a System call

a [[trap]] instruction is called when a system call is invoked to change from user to kernel mode.
the OS pops off register values and store the programs current execution details into the [[process control block ]] (PCB). 
OS then pops off the system call# and paramenters
Then calls the function in kernel using a dispatcher
The return value is then pushed onto the stack
The sceduler decides what process to run next through [[context switch]]
OS switch back to User mode
Reload registers from PCB
Runs next instruction after system call

System Calls are generally expensive because they need to save process state, restart the process state, [[context switch]]/jumping from one address space to another