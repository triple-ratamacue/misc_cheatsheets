# TMUX - A terminal multiplexer

Tmux is a great tool that allows you to create terminal sessions from which you can disconnect without cancelling the processes that are running in it. Really useful if working remotely via ssh, for instance.  

## Sessions
A new tmux session can be created via 

    tmux new -s NAME   


Whilst being in the session (basically, a new terminal), detaching happens via

    CTRL+b, d  

To list all running sessions, type 

    tmux ls  

To open a particular session, type 

    tmux attach -t NAME  

Killing a session happens via 

    tmux kill-session -t NAME  


## Windows
Within a session, it's possible to have multiple windows open at the same time.  
Press 

    CTRL+b 

and one of the following keys:

    c	create new window  
    &	kill current window  
      
    n	switch to next window (cycles through)  
    p	switch to previous window (cycles through)  
    l	switch to previously selected window (not cycling through)  
    0-9 switch to window 0 to 1  
    '	prompt for a window index 
    w	choose window from interactive menue


## Panes
It's also possible to have multiple panes within one window!  
Again, press 

    CTRL+b  

and one of the following keys:

    %	split pane into left and right  
    "	split pane into top and bottom 
    !   break current pane out and into new window  
    x	kill current pane  
       
    arrow	switch to left/right/top/bottom pane  
    q 		display pane indices
    t		show time (exit with q)  
    CTRL+arrow  change size of curent pane  
    {,}		swap current pane with next/previous pane
    
    
   
