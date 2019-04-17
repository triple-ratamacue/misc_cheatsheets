### how to change linux login background
gnome tweaks let me change wallpaper and lock screen background, but not the background of the login screen.  
To replace the rather bleak stock image with a fancy colourful wallpaper, run the following command
```
$ sudo gedit /usr/share/gnome-shell/theme/ubuntu.css
```

and replace lines as follows:
```css

/*#lockDialogGroup {
  background: #2c001e url(resource:///org/gnome/shell/theme/noise-texture.png);
  background-repeat: repeat; }
*/
#lockDialogGroup {
  background: #2c001e url(file:///home/USER/Pictures/Wallpapers/image.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
```
