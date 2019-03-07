# BFD library : Binary File Descriptor library 

The BFD library is used by the linker to access object and archive files. They allow 
the linker to use the same routines to operate on object files whatever the object 
file format, they work like an additional abstraction layer allowing the linker to use 
standard calls for all formats. 

> Note : There is potenciel for information loss between the original file formate and 
what BFD will allow the linker to have access to. [More 
information](https://www.math.utah.edu/docs/info/ld_4.html#SEC21)

It is used by most of the GNU binutils to do low-level manipulation.

## How it works 

When an object file is opened, BFD subroutines automatically determine the *format of 
the input object file*. They then *build a descriptor in memory* with *pointers to 
routines* 
that will be used to access elements of the object file's data structures.

As different information from the the object files is required, BFD reads from 
different sections of the file and processes them. 

_For example_: a very common operation 
for the linker is processing symbol tables. Each BFD back end provides a routine for 
converting between the object file's representation of symbols and an internal 
canonical format. When the linker asks for the symbol table of an object file, it calls 
through a memory pointer to the routine from the relevant BFD back end which reads and 
converts the table into a canonical form. The linker then operates upon the canonical 
form. When the link is finished and the linker writes the output file's symbol table, 
another BFD back end routine is called to take the newly created symbol table and 
convert it into the chosen output format. 

## Fun memories 

A bunch of fun memories with the BFD library.

### According to the README

```
The documentation on using BFD is scanty and may be occasionally
incorrect.  Pointers to documentation problems, or an entirely
rewritten manual, would be appreciated.
```

### My warnings

When trying to open a 

## Sources

https://www.math.utah.edu/docs/info/ld_4.html#SEC21
https://www.gnu.org/software/binutils/binutils.html
https://github.com/Cmiroslaf/BEFA-Library/wiki/GNU-BFD-Lib-Documentation
