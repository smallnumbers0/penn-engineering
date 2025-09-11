consists of function arguments and local variables passed in during a function call. Multiple function calls will keep adding onto the stack. The [[stack pointer]] grows with the stack pointing to the last element added which is also the first element to be popped off. (LIFO)

The memory address that the [[stack pointer]] points at is also the smallest address available of the stack.

=============== Highest Address (0xFFFFFFFF)
|                                  |
|     STACK                 | ← Stack starts here and grows down
|                                  |
|------------------- | ← Stack Pointer (current top of stack)
|                                  |
|  (free space)           |
|                                  |
|------------------- | ← Heap grows up toward higher addresses  
|                                  |
|     HEAP                   |
|                                  |
|------------------- | 
|    DATA                    |
|------------------- | 
|    CODE                    |
=============== Lowest Address (0x00000000)


