process of moving processes or memory pages between physical RAM to Disk to manage memory in the RAM efficiently.

The OS monitors RAM usage and selects less frequently used or inactive processes or [[pages]] to leave the RAM. It takes into account the access frequency, priority level, time since last access.

In the swap out operation, data is moved from RAM to a **swap space** (an area in the disk). Then the [[page table]] is updated by the OS to reflect the new location of the swapped data.

In the swap in operation, data is loaded back into the RAM, potentially displacing other data.

A [[page fault]] can occur if a program attempts to access a memory page that is not loaded into RAM. This triggers a hardware interrupt and allows the OS to handle it.