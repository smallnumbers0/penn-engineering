common interrupts start from a completion of a disk operation, or [[clock pulse]].
the [[OS]] picks up a hardware interrupt and a [[signal]] is delivered to the user process that was waiting for the disk operation

Kernel figures out which process to unblock by the interrupt id to transition the process to the ready state

Other common hardware interrupts include illegal memory access from a user level process

Network messages

in an interrupt, 
1: process running
2: user to kernel 
