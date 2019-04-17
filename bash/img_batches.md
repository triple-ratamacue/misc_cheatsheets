### how to batch process images with imagemagick/mogrify

#### batch resize
```bash
$ mogrify -path small/ -auto-orient -thumbnail 200x *.jpg
```
or 
```bash
$ mogrify -path small/ -resize 200x *.jpg
```
