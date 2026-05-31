How to install package through shell script



\#!/bin/bash



<<comment

&#x20;The shell script takes an any package as argument and it installs it

comment



echo "installing the package $1"



sudo apt-get install $1 -Y



echo "Installed successfully $1"



sudo systemctl status $1





along with this i understood how to remove/delete the installed package

sudo apt purge nginx





\# IF CONDITION

\#!/bin/bash



read -p "Character Name: " name



if \[ $name == "pinda" ]; then

&#x20;       echo "Hamza is a spy"

else

&#x20;       echo "Hamza is not a spy"

fi



i can see the structure of if condition



if condition; then

else 

fi



if block closes with fi



\## now this example of classic finding whether files exists or not



\#!/bin/bash



read -p "enter directory name: " dir

if \[ -d $dir ]; then

&#x20;       echo "exists"

else

&#x20;       echo "not exists"

fi





