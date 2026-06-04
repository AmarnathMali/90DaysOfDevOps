creating backup function/project

cat backup.sh
#!/bin/bash

SOURCE="/home/ubuntu/scripts"
TARGET="/home/ubuntu/package"
FILENAME=$TARGET/backups-$(date +%Y-%m-%d_%H-%M-%S)

echo $FILENAME

now its time do a tar yesterday i missed,

tar -cvzf $FILENAME $SOURCE   -> this command creates compressed tar file, just like windows WinRAR file


tar file creation
cron schedule

crontab -e
vim editor
***** bash /home/ubuntu/backup.sh

stop cron schedule  -> just comment it and save it
watch ls -l -> command each shows each time or checks
