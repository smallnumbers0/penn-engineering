# Three fundamental OS concepts
- Batch Processing
- Multiprogramming
- Virtual Memory

## Batch Processing

The Operating System collects jobs, programs, or commands into batches and processes them sequentially without the need for user interaction
The advantages include increased efficiency and improved resource management through grouping similar items together, higher [[throughput]] by minimizing CPU idle time


## Multiprogramming

The OS loads multiple programs into memory(RAM) simultaneously allowing the CPU to [[context switch]] between programs when one is waiting for I/O operations. 
Utilizes resource sharing and concurrent execution by managing resources among other competing programs to maximize CPU utilization
This allows us to have faster user response times, efficiently use memory, I/O devices, etc

## Virtual Memory

This allows each program in a multiprogramming environment to have its own protected [[virtual memory]] space while sharing a physical memory space. There is an abstraction between a program and physical memory where [[virtual memory]] addresses are translated to physical addresses by the [[Memory Management Unit]]. Memory is broken up into fixed sized blocks called pages in a virtual space and frames in the physical space. The OS maps the page numbers to physical frame numbers using a [[page table]] and monitors when RAM is being running out. [[Swapping]] occurs when moving [[pages]] between the physical RAM and disk.



