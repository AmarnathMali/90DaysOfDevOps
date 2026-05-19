Core Components of Linux
Kernel: it is  the main part of os which talks to Hardware.
shell: the user interface where we wright commands.
user space:  The environment where applications, libraries, and utilities run.
init/systemd: the first process(PID 1) starts by kernel to initilaize user space

**How processes are created and managed**
->In Linux, processes are created using system calls like fork() and exec(), managed by the kernel through scheduling and states,
 and controlled by users with commands such as ps, kill, and top. Each process is uniquely identified by a PID and can run in the foreground or background.

 Process States:
 Created: Data structures initialized.
 Ready: Waiting for CPU time.
 Running: Actively executing.
 Sleeping: Waiting for input/resource.
 Stopped: Paused by user/system.
 Zombie: Finished execution but not cleaned up.
 Orphan: Parent terminated, child still running.
 Terminated: Fully cleaned up.

 todays commands:
 Process Management Tools:
 ps → Show running processes (ps aux).
 top → Real-time CPU/memory usage.
 kill → Terminate a process (kill -9 PID).
 jobs → List background/foreground jobs in shell.

 **df**
 The df command in Linux shows disk space usage for mounted filesystems. It’s short for disk free.
 df → Displays all mounted filesystems with their size, used, and available space.
 df -h → Human-readable format (GB/MB instead of blocks).

 **free**
 The free command in Linux shows memory usage — both RAM and swap. It’s one of the quickest ways to check system health.
 free → Displays memory in kilobytes.
 free -h → Human-readable (MB/GB).

  Swap space → Disk space reserved to hold memory pages when physical RAM is full. Think of it as a backup memory pool.
