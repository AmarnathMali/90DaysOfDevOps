Task 1: Create Files 



created file using touch 

=> touch devops.txt



created file using cat command

=> cat > notes.txt

it opens window where we have to write content after that have to do ctrl+d



create script file

=> vim script.sh 

\-> echo "Hello DevOps"



made permission change to execute

=> chmod 764 script.sh

=> ./script.sh



task 2: Read files

**using head:**



ubuntu@ip-172-31-3-183:\~$ head -n 5 /etc/passwd

root:x:0:0:root:/root:/bin/bash

daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin

bin:x:2:2:bin:/bin:/usr/sbin/nologin

sys:x:3:3:sys:/dev:/usr/sbin/nologin

sync:x:4:65534:sync:/bin:/bin/sync

ubuntu@ip-172-31-3-183:\~$



**tail:**



ubuntu@ip-172-31-3-183:\~$ tail -n 5 /etc/passwd

tokyo:x:1001:1001::/home/tokyo:/bin/sh

berlin:x:1002:1002:berlin,,,:/home/berlin:/bin/bash

chandu:x:1003:1004::/home/chandu:/bin/sh

devu:x:1004:1005::/home/devu:/bin/sh

mallu:x:1005:1006::/home/mallu:/bin/sh



