## howto: repair GRUB
### requirements
- bootable linux live cd/usb

### steps 
#### 1. boot from live cd/usb
Once booted, identify linux partition via 
```
lsblk
```
For this tutorial, I'll assume it resides in /dev/sda3

#### 2. mount linux partition
Next, I'll mount the system partition
```bash
sudo mount /dev/sda3 /mnt
```

#### 3. bind system directories 
Now I need to replace the live distro's sys dirs with the ones from the mounted partition
```
sudo mount --bind /dev /mnt/dev &&
sudo mount --bind /dev/pts /mnt/dev/pts &&
sudo mount --bind /proc /mnt/proc &&
sudo mount --bind /sys /mnt/sys
```

#### 4. move into mounted partition and set as root
before I'm able to install grub, I have to pretend that the mounted partition is the actual root partition of my sys
```
sudo chroot /mnt
```

#### 5. install grub 
this should be self-explanatory
```
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
```
#### 6. exit mounted system and unmount
```
exit &&
sudo umount /mnt/sys &&
sudo umount /mnt/proc &&
sudo umount /mnt/dev/pts &&
sudo umount /mnt/dev &&
reboot
```


