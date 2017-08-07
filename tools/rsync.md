# Rsync Cheatseet
rsync is an extremely versatile tool for synching files and folders between local or local and remote locations.  
In particular for remote backups, rsync has some clear advantages over more well-known tools, such as scp:
- rsync allows to compress files during transfer, saving bandwith  
- rsync keeps track of changes within files between src and dest. This means, if you're transferring large files over the internet and the connection interrupts, you can just resume once the connection is again established and don't have to start from scratch (take this, scp!)  

## Basics 
The usage of rsync couldn't be more straight forward:  
```bash
rsync -ARGS SRC/ DEST/
``` 
copies files from SRC to DEST, under the constraints given by the argument list ARGS. 
Note the trailing slash behind src and dest. Those are important to make sure that only the contents of src are copied into dest, and not the folder itself.  


## Important arguments
rsync has millions of arguments to adapt its functionality to every possible use case. 
Here are the most important ones:
```bash
-a              # archive mode: recurse into directories, preserve permissions, symlinks and time stamps  
-n              # dry-run. "Simulate" the file transfer. Good practice to monitor changes before you apply them  
-v              # verbose mode
-u              # ignore files in dest that have newer time stamp. You only want to apply changes in src to dest!  
-P              # short for --partial and --progress. Allows you to resume interrupted transfers and monitor individual file transfer progress
-h              # make output human readable (e.g. in Kb, Mb etc)  
-e              # specifies remote shell. use "-e ssh" to transfer via ssh (see example 2)  
-z              # compresses files via transmission (saves bandwith)
--relative      # use this if DEST doesn't exist already
--delete        # delete files in DEST that don't exist in SRC anymore!  
--log-file=FILE # logs everything to file FILE. better than "> FILE"   
```

## Example: Local to Local
This line copies everything new from SRC to DEST and deletes files in DEST that don't exist in SRC anymore
```bash
rsync -av --delete /SRC/ /DEST/
```

## Example: Local to Remote
Imagine you're the user "banajoe" and the remote IP is 21.21.21.0
```bash
rsync -av --delete -e ssh /SRC/ banajoe@21.21.21.0:/DEST/
``` 
Done!  
Personally, I prefer the following workflow:  
Use settings to compress the data during transfer and ensure that it's possible to resume interrupted transfers  
1. Do a dry run
```bash
rsync -navuPzh --delete -e ssh /SRC/ banajoe@21.21.21.0:/DEST/ > logfile.txt
```
2. Inspect logfile 
```bash
cat logfile.txt | more
```
3. If satisfied with everything, perform actual file-transfer
```bash
rsync -avuPzh --delete -e ssh /SRC/ banajoe@21.21.21.0:/DEST/ > logfile.txt
```


## Automated Backups 
If you'd like to perform automated backups at a specific time and day every week, use cron!  
1. Edit the cron table for the currently logged in user
```bash
crontab -e
```
Crontab uses the following format:
```

*     *     *   *    *        command to be executed
-     -     -   -    -
|     |     |   |    |
|     |     |   |    +----- day of week (0 - 6) (Sunday=0)
|     |     |   +------- month (1 - 12)
|     |     +--------- day of month (1 - 31)
|     +----------- hour (0 - 23)
+------------- min (0 - 59)
```
2. Once the crontab is opened in vi, insert the following to perform file transfers every weekday at 9pm
```bash
0 21 * * 1-5 rsync -av --delete /SRC/ /DEST/
```

## Advanced example: Snapshot backups
Here's an example script to perform snapshot backups (each backup is written to a new DEST folder, but with hard-links to unchanged files in previous backup)
```bash
#!/bin/bash

# ensure that no rsync process is already running
pkill -9 rsync
# copy old time-stamp 
cp -f ~/BCKP/timestamp.txt ~/BCKP/timestamp_old.txt

# update time stamp
echo `date +”%F--%I-%M%p”` > ~/BCKP/timestamp.txt  

# create log file
touch ~/BCKP/rsync_bckp-`cat ~/BCKP/timestamp.txt`.log

# move the data into newly created destination folder and provide hard link to previous location (with timestamp_old) for snapshop backup
# do also change the permissions of the newly created folder appropriately
rsync -avzhuPR --chmod=Du=rwx,Dgo=rx,Fu=rw,Fgo=r --delete --log-file=BCKP/rsync_bckp-`date +%F--%I-%M%p`.log --link-dest=/home/bananajoe/DEST/`cat ~/BCKP/timestamp_old.txt`  -e ssh home/bananajoe/SRC/ bananajoe@21.21.21.0:~/DEST`date +”%F--%I-%M%p”`/

# scp the log file into the new dest folder
scp ~/BCKP/rsync_bckp-`cat ~/BCKP/timestamp.txt`.log bananajoe@21.21.21.0:~/DEST`date +”%F--%I-%M%p”`/.

```
