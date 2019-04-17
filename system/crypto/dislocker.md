# Dislocker Quick Reference

howto: mount bitlocker-encrypted disk in linux


#### get root access
``` bash
sudo -s
```

#### decrypt the disk

1. create folder for image and mountpoint for content  
``` bash
mkdir /media/USER/diskUnlock /media/USER/diskContent
```

2. determine device name MYDEVICE  
``` bash
fdisk -l
lsblk
```
3. use dislocker to unlock drive. this will place a file called *dislocker-file* into the specified directory. Note that the password will be written to your bash history as cleartext, so you might want to take care of this later..  
``` bash
dislocker -r -V /dev/MYDEVICE/ -uPASSWORD -- /media/USER/diskUnlock/
````

#### mount the image
``` bash
mount -r -o loop /media/USER/diskUnlock/ /media/USER/diskContent/
```

#### once done, tidy up
``` bash
umount /media/USER/disk*
hdparm -y /dev/MYDEVICE # spin down if it was a hdd
```