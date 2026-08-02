
Most common way of supporting concurrent clients is Each client -> its own thread

key challenges -> Making code thread safe threads unnecessarily waits

slows execution , increases complexity

We need to use Mutex and Semaphore to make it thread safe

===================================================
I/O Multiplexing : Async I/O programming 

How to implement it : EPOll, KQUEUE , IOCP

Epoll monitores a lot of file descriptors for new I/O 

event loop not a saparate thread or neather a process it's just a thin layer that just manage I/O


