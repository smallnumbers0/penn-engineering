processes in a pipeline form a group with the same pgid

the [[foreground]] process group is the one that takes all terminal inputs and terminal generated signals giving us [[terminal control]]

Async wait via SIGCHLD is the standard, efficient way to track child state without burning CPU.

A session is the higher-level container that groups your shell and its related jobs.
Sessions provide the higher‑level container for your shell and its jobs.