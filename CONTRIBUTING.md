# Contributor Guide

## Avoid Annotations in Comments

Comments do not need extra formatting such as banners of stars. The generated output
may not even be presented in a fixed-width font, so don't depend on spacing for alignment—godoc, 
like gofmt, takes care of that. The comments are uninterpreted plain text, so HTML and other 
annotations such as _this_ will reproduce verbatim and should not be used. One adjustment godoc 
does do is to display indented text in a fixed-width font, suitable for program snippets. 
The package comment for the fmt package uses this to good effect.


## Comment First Word as Subject

Doc comments work best as complete sentences, which allow a wide variety of automated presentations.
The first sentence should be a summary that starts with the name being declared.


## Good Package Name

It's helpful if everyone using the package can use the same name 
to refer to its contents, which implies that the package name should 
be good: short, concise, evocative. By convention, packages are 
given lower case, single-word names; there should be no need for 
underscores or mixedCaps. Err on the side of brevity, since everyone 
using your package will be typing that name. And don't worry about 
collisions a priori. The package name is only the default name for 
imports; it need not be unique across all source code, and in the 
rare case of a collision the importing package can choose a different 
name to use locally. In any case, confusion is rare because the file 
name in the import determines just which package is being used.


## Single Method Interface Name

By convention, one-method interfaces are named by the method name plus an -er suffix 
or similar modification to construct an agent noun: Reader, Writer, Formatter, CloseNotifier etc.

There are a number of such names and it's productive to honor them and the function names they capture. 
Read, Write, Close, Flush, String and so on have canonical signatures and meanings. To avoid confusion, 
don't give your method one of those names unless it has the same signature and meaning. Conversely, 
if your type implements a method with the same meaning as a method on a well-known type, give it the 
same name and signature; call your string-converter method String not ToString.


