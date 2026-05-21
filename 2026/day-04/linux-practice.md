**Check Running Processes:**



ps aux → Lists all processes with details like PID, CPU%, MEM%, and command.

top or htop → Interactive view of processes, sorted by resource usage.

pgrep → Quickly find process IDs by name, e.g. pgrep nginx.





**🔑 Breaking Down ps aux**

a option → Displays processes from all users, not just the current one.



u option → Shows a user-oriented format, including:



USER (owner of the process)



%CPU and %MEM (resource usage)



START time and COMMAND



x option → Includes processes without a controlling terminal (background daemons, services).



Together, ps aux gives a complete snapshot of system activity.



**2: Inspect a Systemd Service**

**systemctl status nginx**

journalctl -u nginx --since "10 min ago"

journalctl -u nginx -n 20

systemctl restart nginx











Command	Flag	Effect

ls	-a / --all	Show hidden files

ls	-l	Long listing with permissions, size, owner

mkdir	-p	Create parent directories if missing

cp	-v	Verbose output (shows copied files)

rm	-r	Recursive delete (directories + contents)

du	--human-readable	Show disk usage in KB/MB/GB





mnt

Temporary mount point → /mnt is used when you manually mount something (like a USB stick or extra disk).



Manual use → You create a folder inside /mnt (e.g., /mnt/usb) and mount your device there.



Difference Between /bin and /sbin

Directory	Purpose	Examples

bin		Essential user commands available to all users	ls, cp, mv, cat

sbin		System administration commands, usually root-only	shutdown, mount, ifconfig









