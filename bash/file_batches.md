### 1. how to replace string in multiple files 
```
grep -rl 'oldString' . | xargs sed -i 's/oldString/newString/g'
```


### 2. how to rename multiple files 
```
for filename in *PATTN; do echo mv \"$filename\" \"${filename//'foo'/'bar'}\"; done | /bin/bash
```
finds all files in current directory that match \*PATTN and replaces 'foo' in their name with 'bar'.  
Here's an example on how to remove underscores from matlab files 
```
for filename in *mat; do echo mv \"$filename\" \"${filename//'_'/''}\"; done | /bin/bash
```
to test if everything works, forward commandsto text file, before piping the whole thing to bash:
```
for filename in *mat; do echo mv \"$filename\" \"${filename//'_'/''}\"; done > review.txt
```
source:  
http://www.peteryu.ca/tutorials/shellscripting/batch_rename  
