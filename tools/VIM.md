# VI - Text editor
A brief cheatsheet for the VI text editor  
If not indicated otherwise, these commands are executed from within "command mode"  

## Basics

    :		go to command mode
    :q		quit file
    :q!		force quit file
    :wq 	write and quit
    :x		abbreviation of wq

      
## FILES and FOLDERS

    vim	NAME	open file 
    :edit NAME  open file 
    :e CTRL+D	show folder contents
    :Explore	open file explorer 


## PANES 
  
    :sp		split horizontally
    :vs		split vertically 
    CTRL+w	open pane switcher, use arrows to switch panes


## Navigation
Use arrow keys or h,j,k,l to navigate   

    **File**   
    gg		move to first line of file  
    G		move to last line of file  
    :NUMBER	move to line NUMBER  
        
    **Screen**  
    H		move to top of screen  
    M		move to middle of screen
    L		move to bottom of screen    
    
    **Line**  
    0		move to beginning of line  
    $		move to end of line  
    ^		move to first non-blank char (useful for python etc)  
    

## SEARCH

##  EDITING

    u		Undo  
    CTRL+r	Redo  

## INSERT MODE 

    **enter/exit mode:**  
    i		enter insert mode in front of current letter  
    a		enter insert mode behind current letter (append)  
    ESC		exit insert mode  
      
    **replace strings**  
    s/foo/bar/g	replace foo by bar in current line  
    %above 	replace foo by bar in whole file 
    
    


