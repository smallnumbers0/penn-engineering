async software notifiation to a process of an event

software interrupt but can oly be initiated by another process, doesnt have to be the OS

SIG*
signals.h

signal handler is used by a process

SIGINT associates with ctrl c to kill a process

A signal mask can be created by a user level process initially set to 0s. Each process has its own signal mask. If we want to block ctrl c, the system call sigprocmask() indicates that if someone does a ctrlc we will block it

Sigsuspend

WIFSIGNALED(status): True if the child terminated because it received a signal.

WIFSTOPPED(status): True if the child was stopped (not terminated) by a signal such as SIGTSTP from Ctrl‑Z. Indicates a suspended state that can be continued, not a termination.

To terminate use **SIGINT** (Ctrl‑C) or **SIGKILL** (kill -9)