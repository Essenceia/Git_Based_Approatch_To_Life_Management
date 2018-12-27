# Git Pull 

The behavior of the git pull with no arguments varies on the default settings of the pull, you can specify a specific version with `.` : `pull.default`.
This can be configured. 


##Cheat sheet 

- pull = fetch + merge
- pull --rebase = fetch + rebase 
- git pull origin foo = git fetch origin foo; git merge o/foo
- git pull origin bar~1:bugFix =git fetch origin bar~1:bugFix; git merge bugFix
