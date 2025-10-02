The controlling terminal relays signals to the [[foreground]] group. Background jobs that read from the terminal trigger **SIGTTIN** (stopped); background writes may be allowed or blocked with **SIGTTOU**


background relies on signals