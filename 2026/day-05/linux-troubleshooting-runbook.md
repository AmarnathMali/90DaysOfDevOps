\# Linux Troubleshooting Runbook

\## Target Service

sshd (Secure Shell Daemon)



**Step 1: Environment Basics**



***ubuntu@ip-172-31-3-183:\~$ uname -r***

***7.0.0-1004-aws***

***ubuntu@ip-172-31-3-183:\~$ uname -a***

***Linux ip-172-31-3-183 7.0.0-1004-aws #4-Ubuntu SMP PREEMPT Mon Apr 13 13:14:24 UTC 2026 x86\_64 GNU/Linux***

***ubuntu@ip-172-31-3-183:\~$ cat /etc/os-release***

***PRETTY\_NAME="Ubuntu 26.04 LTS"***

***NAME="Ubuntu"***

***VERSION\_ID="26.04"***

***VERSION="26.04 (Resolute Raccoon)"***

***VERSION\_CODENAME=resolute***

***ID=ubuntu***

***ID\_LIKE=debian***

***HOME\_URL="https://www.ubuntu.com/"***

***SUPPORT\_URL="https://help.ubuntu.com/"***

***BUG\_REPORT\_URL="https://bugs.launchpad.net/ubuntu/"***

***PRIVACY\_POLICY\_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"***

***UBUNTU\_CODENAME=resolute***

***LOGO=ubuntu-logo***

***ubuntu@ip-172-31-3-183:\~$***



**step 2: Filesystem sanity**



***ubuntu@ip-172-31-3-183:\~$ mkdir /tmp/runbook***

***ubuntu@ip-172-31-3-183:/$ cp /etc/hosts /tmp/runbook/hosts-copy \&\& ls -l /tmp/runbook***

***total 4***

***-rw-r--r-- 1 ubuntu ubuntu 221 May 22 10:42 hosts-copy***



**Step 3: CPU \& Memory Snapshot**



**ubuntu@ip-172-31-3-183:/tmp/runbook$ top**

top - 11:14:46 up  1:12,  2 users,  load average: 0.00, 0.00, 0.00

Tasks: 119 total,   1 running, 118 sleeping,   0 stopped,   0 zombie

%Cpu(s):  0.3 us,  0.5 sy,  0.0 ni, 99.0 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st

MiB Mem :    908.7 total,    327.4 free,    321.5 used,    369.8 buff/cache

MiB Swap:      0.0 total,      0.0 free,      0.0 used.    587.2 avail Mem



&#x20;   PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND

&#x20;    38 root      20   0       0      0      0 S   0.3   0.0   0:00.15 kcompactd0

&#x20;   129 root      19  -1   50244  16300  14928 S   0.3   1.8   0:01.00 systemd-journal

&#x20;  1304 ubuntu    20   0   18728   8804   6080 S   0.3   0.9   0:03.11 sshd-session

&#x20;     1 root      20   0   25212  16044  10904 S   0.0   1.7   0:02.22 systemd

&#x20;     2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd

&#x20;     3 root



**ubuntu@ip-172-31-3-183:/tmp/runbook$ free -h**

&#x20;              total        used        free      shared  buff/cache   available

Mem:           908Mi       321Mi       326Mi       2.7Mi       370Mi       587Mi

Swap:             0B          0B          0B

ubuntu@ip-172-31-3-183:/tmp/runbook$ ^C



**ubuntu@ip-172-31-3-183:/tmp/runbook$ ps -o pid,pcpu,pmem,comm -p $(pidof sshd)**

&#x20;   PID %CPU %MEM COMMAND

&#x20;  1012  0.0  0.8 sshd



**step 4: Disk \& IO checks**



df -h -> 👉 Shows disk usage in human‑readable format.

du -sh /var/log  -> 👉 Summarizes the size of the /var/log directory.



df	Disk Free  Check if a disk/partition is running out of space.

du	Disk Usage Find which directories or files are consuming space.

iostat   Shows how much time the CPU spends in user mode, system mode, idle, and waiting for I/O.



**ubuntu@ip-172-31-3-183:\~$ iostat**

Linux 7.0.0-1004-aws (ip-172-31-3-183)  05/22/26        \_x86\_64\_        (2 CPU)



avg-cpu:  %user   %nice %system %iowait  %steal   %idle

&#x20;          0.34    0.00    0.48    0.03    0.01   99.14



Device             tps    kB\_read/s    kB\_wrtn/s    kB\_dscd/s    kB\_read    kB\_wrtn    kB\_dscd

loop0             0.02         0.59         0.00         0.00       4435          0          0

loop1             0.01         0.09         0.00         0.00        688          0          0

loop2             0.01         0.05         0.00         0.00        372          0          0

loop3             0.00         0.00         0.00         0.00         18          0          0

nvme0n1           3.51        39.95        49.43         0.00     301366     372878          0



vmstat -> virtual memory



**ubuntu@ip-172-31-3-183:\~$ vmstat**

procs -----------memory---------- ---swap-- -----io---- -system-- -------cpu-------

&#x20;r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st gu

&#x20;2  0      0 327420  19844 363440    0    0    40    49  127    0  0  0 99  0  0  0



procs -----------memory---------- ---swap-- -----io---- -system-- -------cpu-------

&#x20;r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st gu

&#x20;2  0      0 327420  19844 363440    0    0    40    49  127    0  0  0 99  0  0  0





**🌐 Network Commands**

**1. ss -tulpn**

ss → Socket statistics tool (modern replacement for netstat).



Flags:



\-t → Show TCP sockets.



\-u → Show UDP sockets.



\-l → Show only listening sockets (waiting for connections).



\-p → Show the process using the socket (needs root for full info).



\-n → Show numeric addresses/ports (don’t resolve names).



So ss -tulpn = “Show all listening TCP/UDP sockets with process info, in numeric form.”



**ubuntu@ip-172-31-3-183:\~$ ss -tulpn**

Netid          State           Recv-Q          Send-Q                       Local Address:Port                    Peer Address:Port          Process

udp            UNCONN          0               0                                127.0.0.1:323                          0.0.0.0:\*

udp            UNCONN          0               0                               127.0.0.54:53                           0.0.0.0:\*

udp            UNCONN          0               0                            127.0.0.53%lo:53                           0.0.0.0:\*

udp            UNCONN          0               0                        172.31.3.183%ens5:68                           0.0.0.0:\*

udp            UNCONN          0               0                                    \[::1]:323                             \[::]:\*

tcp            LISTEN          0               4096                         127.0.0.53%lo:53                           0.0.0.0:\*

tcp            LISTEN          0               4096                            127.0.0.54:53                           0.0.0.0:\*

tcp            LISTEN          0               128                              127.0.0.1:6010                         0.0.0.0:\*

tcp            LISTEN          0               4096                               0.0.0.0:22                           0.0.0.0:\*

tcp            LISTEN          0               128                                  \[::1]:6010                            \[::]:\*

tcp            LISTEN          0               4096                                  \[::]:22                              \[::]:\*





curl → Designed to talk to web servers (HTTP/HTTPS).

Port 22 → Reserved for SSH (Secure Shell), not HTTP.







ubuntu@ip-172-31-3-183:\~$ **telnet localhost 22**

Trying 127.0.0.1...

Connected to localhost.

Escape character is '^]'.

SSH-2.0-OpenSSH\_10.2p1 Ubuntu-2ubuntu3



The **ping** command in Linux is used to test network connectivity between your machine and another host.





**ubuntu@ip-172-31-3-183:\~$ ping -c 4 google.com**

PING google.com (142.250.207.78) 56(84) bytes of data.

64 bytes from pnmaaa-bd-in-f14.1e100.net (142.250.207.78): icmp\_seq=1 ttl=116 time=13.1 ms

64 bytes from pnmaaa-bd-in-f14.1e100.net (142.250.207.78): icmp\_seq=2 ttl=116 time=13.1 ms

64 bytes from pnmaaa-bd-in-f14.1e100.net (142.250.207.78): icmp\_seq=3 ttl=116 time=13.2 ms

64 bytes from pnmaaa-bd-in-f14.1e100.net (142.250.207.78): icmp\_seq=4 ttl=116 time=13.1 ms



\--- google.com ping statistics ---

4 packets transmitted, 4 received, 0% packet loss, time 3004ms

rtt min/avg/max/mdev = 13.103/13.143/13.223/0.047 ms





**Logs**



journalctl → Queries the systemd journal (structured logs).



**ubuntu@ip-172-31-3-183:\~$ journalctl -u sshd -n 50**

\-- No entries --



tail → Displays the last lines of a file.

Flags:

\-n 50 → Show the last 50 lines.



**ubuntu@ip-172-31-3-183:\~$ tail -n 50 /var/log/auth.log**

2026-05-22T12:24:35.233330+00:00 ip-172-31-3-183 sshd-session\[39409]: Invalid user ftpuser from 83.248.155.53 port 46954

2026-05-22T12:24:36.306317+00:00 ip-172-31-3-183 sshd-session\[39409]: error: maximum authentication attempts exceeded for invalid user ftpuser from 83.248.1.53 port 46954 ssh2 \[preauth]

2026-05-22T12:24:36.306432+00:00 ip-172-31-3-183 sshd-session\[39409]: Disconnecting invalid user ftpuser 83.248.155.53 port 46954: Too many authentication flures \[preauth]

2026-05-22T12:24:38.320575+00:00 ip-172-31-3-183 sshd-session\[39423]: Invalid user ftpuser from 83.248.155.53 port 47504

2026-05-

