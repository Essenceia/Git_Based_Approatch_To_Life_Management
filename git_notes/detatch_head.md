# HEAD 

HEAD is a symbolic name for the currently checked out commit ( or branch )  ~ 
essentially what commit 
you're working on top of ~. 

> P.S : IT'S A POINTER !!! 

## Detaching HEAD

Detaching HEAD <=> attaching it to a commit instead of a branch.

For example  
```bash 
# HEAD -> master -> C1
git checkout C1
# HEAD -> C1
```
Now HEAD and master are independant so if you commit master then HEAD will not be 
tracking the most recent commit. 
