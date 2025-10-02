region of [[virtual memory]] where the [[OS]] uses to dynamically allocate memory. In C programming, calls such as malloc(numBytes) will see the number of bytes needed from the parameter and finds a space in the heap for the number of bytes. If there is not enough space, the OS dynamically adds more heap. 

Example of dynamically allocating memory in heap:
char* cArray = (char*) malloc (1024 * sizeof(char)); 
creates a pointer cArray
malloc finds 1024 consecutive bytes of space in the heap
(char* ) is a [[typecast]] that tells the [[compiler]] that the allocated memory should be treated as an array of chars


