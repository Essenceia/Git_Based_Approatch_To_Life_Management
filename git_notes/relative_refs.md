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
## Additional information on `^`

Like the ~ modifier, the ^ modifier also accepts an optional number after it.

Rather than specifying the number of generations to go back (what ~ takes), the 
modifier on ^ specifies which parent reference to follow from a merge commit. Remember 
that merge commits have multiple parents, so the path to choose is ambiguous.

Git will normally follow the "first" parent upwards from a merge commit, but specifying 
a number with ^ changes this default behavior.

Example : 
```
	*
	|
    C1	*--------------* C0 
	|	       |
	|              |
	------*--------
	      |
	     HEAD
```

If I was to `git chekout HEAD^` which branch would be my HEAD's parent, C0/1 ?
To not give any ambiguity I can select it expliciatly `git checkout HEAD^0`.

> P.S : You can stack `~` and `^` together to make sure nobody else understands what 
you are doing.
