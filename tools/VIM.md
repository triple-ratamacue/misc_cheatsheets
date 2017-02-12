# VI - Text editor
A brief cheatsheet for the VI text editor  
If not indicated otherwise, these commands are executed from within "command mode"  

If total newbie, just type "vimtutor" in bash and follow instructions  


<!-- vim-markdown-toc GFM -->
* [BASICS](#basics)
* [INSERT MODE](#insert-mode)
* [FILES and FOLDERS](#files-and-folders)
* [PANES](#panes)
* [NAVIGATION](#navigation)
* [SEARCH](#search)
* [REPLACE](#replace)
* [EDITING](#editing)

<!-- vim-markdown-toc -->
## BASICS

    :		go to command mode
    :q		quit file
    :q!		force quit file
    :wq 	write and quit
    :x		abbreviation of wq

      
## INSERT MODE 

    **enter/exit mode:**  
    i		enter insert mode in front of current letter  
    a		enter insert mode behind current letter (append)  
    ESC		exit insert mode  

## FILES and FOLDERS

    vim	NAME	open file 
    :edit NAME  open file 
    :e CTRL+D	show folder contents
    :Explore	open file explorer 
    

## PANES 
  
    :sp		split horizontally
    :vs		split vertically 
    CTRL+w	open pane switcher, use arrows to switch panes


## NAVIGATION
Use arrow keys or h,j,k,l to navigate   

**File**   
    
    gg		move to first line of file  
    G		move to last line of file  
    :NUMBER	move to line NUMBER  
        
**Buffers**
    
    Convenient way to navigate between recently opened files.
       
    :b 1	open file with index 1
    :ls		list recently opened files with indices j
    
    
**Screen**  
    
    H		move to top of screen  
    M		move to middle of screen
    L		move to bottom of screen    
    
**Line**  
    
    0		move to beginning of line  
    $		move to end of line  
    ^		move to first non-blank char (useful for python etc)  

**Word**
      
    w		move to next word
    b		move to previous word
    e		move to end of current word
        
   
**Character**

    
    f{		jump forward to character {
    t{		jump forward to place in front of charater {

## SEARCH
    
    /foo	search for foo in text after cursour  
    ?foo	search for foo in text before cursor  
    n		move cursor to next occurence of foo  
    N 		move cursor to previous occurence of foo  


## REPLACE
    
   
    **replace strings**  
    s/foo/bar/g	replace foo by bar in current line  
    %above 	replace foo by bar in whole file 
    

##  EDITING

    u		Undo  
    CTRL+r	Redo  
    o		open new line below
    SHIFT+o	open new line above
    p		paste behind cursor
    SHIFT+p	paste above cursor

**Delete**
    
    Note: all deleted items can be pasted 
    dd		delete current line	      
    5dd		delete next five lines (or whichever number you type in)
    dw		delete word
    x		delete character
      
**Yank**
    
    yy		yank current line
    5yy		yank next five lines, including current one
    yw		yank current word
    
**Replace**
    
    r		replace character
    cw		change word
    
**Comment/Uncomment**

Comment:    
  
    1. Go to first line of block you'd like to comment out  
    2. Press *CTRL+v* to enter visual mode  
    3. Use arrow keys to move down until last line of block   
    4. Press *Shift+i* to enter insert mode  
    5. Type comment char, e.g. *#*  
    6. Press *ESC*, hang on for a sec, and enjoy the result  

Uncomment:    
    
    1. Go to first line of block to uncomment  
    2. Press *CTRL+v* to enter visual mode  
    3. Use arrow keys to select lines you'd like to change  
    4. Press *Shift+i* to enter insert mode  
    5. Type *d* or *x* to delete  
    6. Enjoy  

**Fold, Unfold**
  
Make sure to add
    
    set foldmethod=indent
    set foldlevel=99

to your .vimrc

    za		fold/unfold current line
    zo		unfold one under cursor
    zO		unfold all under cursor
    zc		fold one under cursor
    zC		fold all under cursor
   

