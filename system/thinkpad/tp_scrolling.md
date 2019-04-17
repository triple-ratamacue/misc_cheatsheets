### : two-finger scrolling after resume
due to bug in 18.04, I need to change grub config as follows:
```
vi /etc/default/grub
```
change the line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash psmouse.synaptics_intertouch=0"
```

then
```
sudo update-grub
```
Voilà
