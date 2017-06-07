# Howto: Mount luks-encrypted LVM partition in Linux
Scenario: You exchanged your old linux hdd for a new one and are now struggling to access the data on the old disk, which is fully encrypted with LUKS and managed via LVM.

#### identify mounted disks
``` bash
fdisk -l 
lsblk
```

#### open luks partition (with chosen name, here 'myDrive')
``` bash
cryptsetup luksOpen /dev/DISKID/ myDrive
```

#### obtain list of logical volumes, volume groups and UUIDs
``` bash
pvs       # disk identified by name set above (here 'myDrive')
lvdisplay # also useful
vgdisplay # provides UUID
```

#### if necessary: rename volume group 
``` bash
vgrename UUID newGroupName # this renames 
vgchange -ay newGroupName  # this activates the vg
lvscan                     # this shows if state is indeed active
```

#### mount LVM partition
``` bash
lvdisplay /dev/GROUPNAME # shows logical volumes in group, allows you to determine which disk to mount (have a look at row 'LV Name')
mount /dev/GROUPNAME/DISKNAME /media/USER/MOUNTDIR
```

#### once done: unmount and spin down hdd, close luks
``` bash
umount /media/USER/MOUNTDIR
vgchange -an newGroupName
cryptsetup luksClose myDrive
hdparm -y /dev/DISKID
```