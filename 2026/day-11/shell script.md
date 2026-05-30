The long form of Bash is Bourne-Again SHell



\#!/bin/bash -> shebang



why shell script

=> to do DevOps automation



whoami gives username

printenv -> where user value is defined

and all environment variables are defined in capital letters in key-pair structure. we can use those variables in shell script. ($USER)



**Variables :**



\#!/bin/bash

name="shreyash"

echo "Hello $name"

echo "my logged in user is $USER"



so here name act as variable which stores the value and $variable which means ($name) act as placeholder.



now how to take input from terminal, for that we have read command

read -p "enter your name: " name



\-p -> to read from prompt



comment:



\#single line comment

<< multi line comment

>>



argument:



argument is keyword which written after the file name



echo "first argument is $1"

echo "second argument is $2"



