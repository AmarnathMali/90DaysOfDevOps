User Permission/Switch User:



su root    -> su stands for switch user, but when we do it asks for password



/etc/sudoers   -> this is file where, the rules are written who can do super user work



sudo su -> it opens root folder 

whoami -> root



how the ubuntu is user, like that we can create new user

sudo useradd Tokyo   -> hear i kept username as Tokyo



these new user will create home folder just like ubuntu

sudo useradd -m Tokyo  -> -m creates folder in home directory -> this command helps to create user

to switch user to Tokyo

sudo su Tokyo,



now we can do by 'adduser' command also, but it asks password we have to set it.

sudo adduser berlin

password:

retype-password: 

once we set password we can switch through su command, neet to type password without sudo

