ubuntu@ip-172-31-3-183:\~$ pwd

/home/ubuntu

ubuntu@ip-172-31-3-183:\~$ touch notes.txt

ubuntu@ip-172-31-3-183:\~$ echo "Line 1" > notes.txt

ubuntu@ip-172-31-3-183:\~$ cat notes.txt

Line 1

ubuntu@ip-172-31-3-183:\~$ echo "Line 2" >> notes.txt

ubuntu@ip-172-31-3-183:\~$ cat notes.txt

Line 1

Line 2

ubuntu@ip-172-31-3-183:\~$ echo "Line 3" | tee -a notes.txt

Line 3

ubuntu@ip-172-31-3-183:\~$ cat notes.txt

Line 1

Line 2

Line 3

ubuntu@ip-172-31-3-183:\~$ head -n 2 notes.txt

Line 1

Line 2

ubuntu@ip-172-31-3-183:\~$ head -n 2 notes.txt

Line 1

Line 2

ubuntu@ip-172-31-3-183:\~$ head -n 1 notes.txt

Line 1

ubuntu@ip-172-31-3-183:\~$ head -n 3 notes.txt

Line 1

Line 2

Line 3

ubuntu@ip-172-31-3-183:\~$ tail -n 2 notes.txt

Line 2

Line 3

ubuntu@ip-172-31-3-183:\~$

\------------------------------------------------

echo "Line 3" makes the text.



The pipe | sends that text forward.



tee writes it both to the screen and to a file.



\-a tells tee to append instead of overwrite.



