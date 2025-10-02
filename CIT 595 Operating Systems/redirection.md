ls -> stdout -> monitor

ex: ls > out.txt

storing the output of ls to a text file

cat waits for STDIN
ex: cat < Makefile
Makefile here is redirected as stdin into cat command

dup2 - duplicate one file descriptor on another

stdin/stdout is [[process]] specific

new_stdout = open("new_stdout", O_WRONGLY | O_CREAT, 0644);
dup2(new_stdout, STDOUT_FILENO);
write(STDOUT_FILENO, "Hello World!!!", 14);

STDOUT_FILENO - displays on monitor
New_stdout - goes to disk 

