# Reversing changes in git

There are two primary ways to undo changes in git : `git reset` and `git revert`.

## `Git Revert`

Reverts changes by moving the branch reference backwads in time to an older commit. 
> Rewriting history.
This is done by introducing a new commit that introduces changes that are the exact 
revers of the commit you reverted. :smile: 
This can be shared to remote. 

## `Git Reset`

Moves the branch backwards in history as if the commit had never been made in the first 
place. 
The problem with this is that this can't be shared : you can't rewrite the remote's 
history to to share this changes with remote you should have been using revert.
