Job control centers on [[**process]] groups**. A [[pipe]]line forms one group; the leftmost command is the leader, and the **PGID equals the leader’s PID**.

[[Signal]]s can target the whole group by using a negative PGID, so Ctrl‑C or kill can terminate all pipeline members at once.

Blocking waits (synchronous) make the parent stop until children finish—fine for simple foreground runs, wrong for background. Asynchronous handling uses **SIGCHLD**: when a child stops or exits, the parent’s handler performs **non‑blocking waitpid**, checks status with macros like WIFSTOPPED and WIFSIGNALED, and cleans up. This avoids busy‑waiting and lets the shell remain responsive while managing multiple jobs concurrently.