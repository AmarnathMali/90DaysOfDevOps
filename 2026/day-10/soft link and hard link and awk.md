In Linux, a hard link is another name for the same file (sharing the same inode and data), while a soft link (symbolic link) is more like a shortcut pointing to the file’s path. Hard links survive even if the original file is deleted, but soft links break if the target file is removed.



so i create soft link,



ln -s that\_file\_path  new\_path





ln -s soft/sf-demo.txt sf



when we call that sf it will show the data from sf-demo.txt



**soft link:**

ln -s soft/sf-demo.txt sf



**hard link:** 



it is also same as soft link but if we deleted hard-link created one, it will not delete the orginal file.



mkdir -p dir1/dir2/                           -> -p : it creates parent directory

echo "hello" >> dir1/dir2/hello-h.txt

ln \~/dir1/dir2/hello-h.txt hard-link



removed hard-link

rm hard-link

cat dir1/dir2/hello-h.txt

=>hello hello





**awk:**

awk '{print $1}' hello.txt

awk '{print}' hello.txt

awk '{print $1, $4}' hello.txt



The awk command is a powerful text-processing tool in Linux that lets you filter, format, and analyze text files line by line and column by column.





