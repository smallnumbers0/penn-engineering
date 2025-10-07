interleaving instructions across threads can cause incorrect results or race conditions

[[race conditions]] can create bugs that are hard to reproduce due to processes and threads executing concurrently running cpu bursts on shared data structures

critical section is a code region where shared resources are read or modified. 

Mutual exclusion allows one thread to be uninterrupted and finish during this critical section.

Example of thread interleaving:

```
Thread 1: V = V + 1

move V to R0 -> increment R0 

context switch to thread 2

Thread 2: V = V + 1

move V To R1 -> increment R1 

context switch thread 1

Thread 1: V = V + 1

move R0 to V

context switch thread 2

move R1 to V

This is a problem because they are interweaved causing wrong output
```

[[synchronization]] 

Three ways to approach mutual exclusion:
Disabling interrupts
Busy Waiting with shared Variables
Peterson's Solution

### Disabling interrupts

- Turns off interrupts when thread enters a critical section, and turns it back on after it leaves.
- This works because context switches are triggered by interrupts. If there are no interupts, then there are no context switches during the critical section

- Overkill: freezing the entire OS scheduling, not just the threads that are fighting for critical section
- Bad for multicore CPUs: disabling interrupts on one CPU doesnt sto other cores from running other threads concurrently, interleaving can still happen across cores.
- Too much global effect for a local critical section need

clock interrupt is a periodic timer that fires at regular intervals prompting the OS to regain control from whatever code is running. Each interrupt the OS updates timekeeping and manages timers and runs the scheduler to do preemptive multitasking to decide if the current thread's time slice is over or if another should run. 
clock interrupts arrive between instructions and cause context switches which interferes with mutual exclusion. 
We should turn clock interrupt off to protect a critical section

### Busy Waiting

- looping repeatedly checking a condition in order to enter a critical section. The downside is that this wastes CPU cycles.
A cpu cycle is one tick of a processor's internal clock where it carries out an instruction.
- When both flags are true on both threads, it can cause deadlock
- a shared variable turn wastes CPU resources
- When both flags are false this can violate mutual exclusion as both flags can be turned true and both enter critical section.
### Peterson's solution

- software only mutual exclusion for two processes using atomic read/writes
atomic means the values stay consistent for both processes
- Involves a flag[2] and a shared turn variable where flag[i] is true if process wants to enter critical section and turn indicates whose turn it is to resolve a tie.
- This allows both processes to start off as true in the race, but whoever first writes turn gives the other process priority ensuring only 1 process enters the critical section preventing a deadlock.
The cons:
- still busy waiting and wastes cpu cycles
- limited to 2 threads, anymore threads makes it hard

```
// Process i (i = 0 or 1). Let me = 1 - i

// 1) Declare intent to enter the critical section
//    Set our flag to true so the other process knows we want in.
flag[i] = true

// 2) Yield priority to the other process via 'turn'
//    This creates a deliberate race: if both want in, the last writer
//    gives the other process the priority, ensuring only one proceeds.
turn = me

// 3) Busy-wait until it’s safe to enter
//    We wait only if BOTH conditions hold:
//      - The other process currently wants the critical section (flag[me] == true)
//      - And it is currently the other’s turn (turn == me)
//    If either condition is false, we can proceed.
while (flag[me] == true && turn == me) {
    // spin (do nothing)
}

// 4) Enter the critical section
//    At this point, mutual exclusion holds: only one process can be here.
critical_section()

// 5) Exit: clear our intent
//    Signal that we no longer need the critical section, letting the other in.
flag[i] = false

// 6) Remainder section (non-critical work can be done here)
remainder_section()

```

Its better to use Test and set lock (A hardware suppoerted atomic instruction) using blocking sycnhronization, primitives (mutex, semaphores, condition variables) to avoid spin and generalize beyong 2 threads. 
### **mutual exlcusion toolkit**

mutual exclusion means only one thread  can enter a critical section when modifying a shared state to prevent race conditions

critical section includes codes that accesses shared variables where multiple threads are able to update the shared variables

V = V + 1. can be broken down into 3 instructions
move V from memory to Register(RAM -> CPU)
increment Register(CPU)
move value from Register back to memory at V (CPU -> RAM)

Thread 1,2,3,...n can update V.

instruction interleaving can cause non-determinism and create bugs/incorrect results

### Solution 1 for mutual exlcustion
avoid race conditions by disabling context switching when a process is in [[critical section]]
disable intterupts to turn off context siwtching at beginning and end of critical section - prvents clock interupts so scheduler is not involved

critical section means a piece of code where only one process can run

Downsides: 
- Overkill

### solution 2 
shared variable: turn

p1 turn  = 0

p2 turn = 1

### downside of peterson solution:
bbusy waits use too many resources
hard to implment for more than 2 processes



[[Peterson's solution]] 
Does not work on multiple core. 
only works for 2 threads

leverages atomjic operations that compile to single cpu instructions avoiding multiple instruction races

Why busy waiting is bad

wastes cpu resources (cpu cycles)

potential starvation - a thread can be stuck outside consuming cpu cycles in a busy wait while another slow thread is slowly making progress in its critical section


Test and set lock
on most cpus today

Hardware solution 

has a memory location for each critical section (0 or 1) and a register R = M, M = 1, M = mutex
0 means unlocked(no thread in CS), 1 means locked (thread in CS)


Lock -> TSL R, M
if R == 1, take a step back and retry
if R == 0, we aqcuire the lock and enter critical section
unlock M = 0

We have 2 or more threads ->
Thread 1 performs TSL where M is 0 and copies 0 to register and sets M = 1 to lock
Thread 2 performs TSL and sees R == 1 so it busy waits until M is 0 or unlocked
After M = 0 (unlocks) the next thread can run its critical section















