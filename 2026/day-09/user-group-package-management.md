=======================27/5/2026========================



i have created user just like ubuntu, i have used this command

sudo useradd -m chandu

sudo useradd -m devu

sudo useradd -m mallu



verified using this command

cat /etc/passwd

created user are scene



and i have created two groups developer and devops



sudo groupadd devops

sudo groupadd developer



and i verified using command

cat /etc/group



created group are able to view



now, i try to add first two user to developer group and one to devops



sudo gpasswd -a chandu developer

sudo gpasswd -a devu developer

sudo gpasswd -a mallu devops



i verified these users in group by using this command

cat /etc/group



\*\*one more interesting thing whenever we create user that time group also creates with that name .\*\*



\##File permission



\-rw-rw-r-- 1 ubuntu ubuntu 0 May 27 14:24 hello.txt

|-rw-rw-r--|1|ubuntu|ubuntu|0|May 27 14:24|hello.txt|
|-|-|-|-|-|-|-|
|file permission|Number of hard links|user|group|size of file in byte|creation date|file name|





if it starts with "-" then file, "d" means directory, if it is "l" then link.



in file permission from last

last three: r-- : other permission is just read its value is 4

middle three: rw-: Group permission: read and write, 6

first three except first dash: rw- : user permission: 6

read(r) = 4

write(w) = 2

execute(x) = 1



\-----------------

i have created one directory

mkdir devops-project

under this created one file hello.txt



now i did ls -l the permission of files are default

and we changed to rwx to all

chmod 777 hello.txt



now i did the ls  -l



**ubuntu@ip-172-31-3-183:\~/devops-project$ chmod 777 hello.txt**

**ubuntu@ip-172-31-3-183:\~/devops-project$ ls -l**

**total 0**

**-rwxrwxrwx 1 ubuntu ubuntu 0 May 27 14:24 hello.txt**

**ubuntu@ip-172-31-3-183:\~/devops-project$**



here user is ubuntu i try to change the owner to chandu.



sudo chown chandu hello.txt



**ubuntu@ip-172-31-3-183:\~/devops-project$ sudo chown chandu hello.txt**

**ubuntu@ip-172-31-3-183:\~/devops-project$ ls -l**

**total 0**

**-rwxrwxrwx 1 chandu ubuntu 0 May 27 14:24 hello.txt**

**ubuntu@ip-172-31-3-183:\~/devops-project$**





now i try t change the group name also



**sudo chgrp devops hello.txt**



i verified using ls -l command



**ubuntu@ip-172-31-3-183:\~/devops-project$ ls -l**

**total 0**

**-rwxrwxrwx 1 chandu *ubuntu* 0 May 27 14:24 hello.txt**



**ubuntu@ip-172-31-3-183:\~/devops-project$ sudo chgrp chandu hello.txt**

**ubuntu@ip-172-31-3-183:\~/devops-project$ ls -l**

**total 0**

**-rwxrwxrwx 1 chandu *chandu* 0 May 27 14:24 hello.txt**





\# package management/installer



ubuntu - apt/apt-get

centOs - yum

RHFL - rpm/dnf

MacOS - brew



i started doing

sudo apt-get update



It only downloads the latest list of available packages and their versions from the internet.



sudo apt-get upgrade



This uses the new list to see which of your installed packages have newer versions.

It then downloads and installs those actual package updates.



Now i want to download and install nginx

sudo apt-get install nginx



**what is nginx?**

Nginx is high-performance web server software that acts as a secure traffic cop for the internet.

It sits in front of your applications to direct incoming user requests, protect your backend servers from direct exposure, and balance heavy traffic so your website never crashes.



**# Process Management:(systemctl/service)**

now i wann check nginx status



systemctl status nginx



**ubuntu@ip-172-31-3-183:\~/devops-project$ systemctl status nginx**

**● nginx.service - A high performance web server and a reverse proxy server**

&#x20;    **Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: enabled)**

&#x20;    **Active: active (running) since Mon 2026-05-25 12:52:35 UTC; 2 days ago**

&#x20;**Invocation: 2885b147ab3e490c88ae0421f20ab82d**

&#x20;      **Docs: man:nginx(8)**

&#x20;  **Main PID: 660 (nginx)**

&#x20;     **Tasks: 3 (limit: 627)**

&#x20;    **Memory: 4.7M (peak: 5.2M)**

&#x20;       **CPU: 98ms**

&#x20;    **CGroup: /system.slice/nginx.service**

&#x20;            **├─660 "nginx: master process /usr/sbin/nginx -g daemon on; master\_process on;"**

&#x20;            **├─669 "nginx: worker process"**

&#x20;            **└─670 "nginx: worker process"**



it shows this is active running 3 tasks, process id 660, memory, cpu etc.



now i try to stop it, using the command

systemctl stop nginx



\-- it asked password so it failed, for this we use sudo



sudo systemctl stop nginx



**ubuntu@ip-172-31-3-183:\~/devops-project$ sudo systemctl stop nginx**

**ubuntu@ip-172-31-3-183:\~/devops-project$ systemctl status nginx**

**○ nginx.service - A high performance web server and a reverse proxy server**

&#x20;    **Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: enabled)**

&#x20;    **Active: inactive (dead) since Wed 2026-05-27 15:10:02 UTC; 7s ago**

&#x20;  **Duration: 2d 2h 17min 27.457s**

&#x20;**Invocation: 2885b147ab3e490c88ae0421f20ab82d**

&#x20;      **Docs: man:nginx(8)**

&#x20;   **Process: 43490 ExecStop=/sbin/start-stop-daemon --quiet --stop --retry QUIT/5 --pidfile /run/nginx.pid (code=exited, status=0/SUCCESS)**

&#x20;  **Main PID: 660 (code=exited, status=0/SUCCESS)**

&#x20;  **Mem peak: 6.6M**

&#x20;       **CPU: 111ms**



same way we can use service

**service nginx status**

**sudo service nginx start**

**sudo service nginx stop**





and the nginx file html file is present in

/var/www/html

&#x20;

