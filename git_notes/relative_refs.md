# Relative refs

Refs are like hash keys to a specific commit's data and relative refs are like abriged 
versions of the key. 

- `^` move upward one commit at a time
- `~<num>` move upward a number of commits 

Example
```bash 
# checkout to the first parent of master
git checkout master^

# checkout to the grandparent of master
git checkout master^^
```
An you guessed it the HEAD was moved around to point to the parent/grandparent of 
master. Did I forget to mention that git is simply a directed acyclic graph. 

```
git checkout master^

	HEAD		master
	 | 		  |
*--------*----------------*
      (master^)
```

The problem is that you can't really navigate backwards easily youe tree without 
stacking up the `^` or giving `~<num>` a big number if you keep using master as an 
ankor so try using HEAD instead for more flexibility. 
```bash 
git checkout HEAD^
```
