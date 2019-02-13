Want to contribute? Great: read the page (including the small print at the end).

# Before you contribute

As an individual, sign the [Google Individual Contributor License
Agreement](https://cla.developers.google.com/about/google-individual) (CLA)
online. This is required for any of your code to be accepted.

Before you start working on a larger contribution, get in touch with us first
through the issue tracker with your idea so that we can help out and possibly
guide you. Coordinating up front makes it much easier to avoid frustration later
on.

# Development

Make sure `GOPATH` is set in your current shell. The common way is to have
something like `export GOPATH=$HOME/gocode` in your `.bashrc` file so that it's
automatically set in all console sessions.

To get the source code, run

```
go get github.com/google/pprof
```

To run the tests, do

```
cd $GOPATH/src/github.com/google/pprof
go test -v ./...
```

When you wish to work with your own fork of the source (which is required to be
able to create a pull request), you'll want to get your fork repo as another Git
remote in the same `github.com/google/pprof` directory. Otherwise, if you'll `go
get` your fork directly, you'll be getting errors like `use of internal package
not allowed` when running tests.  To set up the remote do something like

```
cd $GOPATH/src/github.com/google/pprof
git remote add aalexand git@github.com:aalexand/pprof.git
git fetch aalexand
git checkout -b my-new-feature
# hack hack hack
go test -v ./...
git commit -a -m "Add new feature."
git push aalexand
```

where `aalexand` is your GitHub user ID. Then proceed to the GitHub UI to send a
code review.

# Code reviews

All submissions, including submissions by project members, require review.
We use GitHub pull requests for this purpose.

The pprof source code is in Go with a bit of JavaScript, CSS and HTML. If you
are new to Go, read [Effective Go](https://golang.org/doc/effective_go.html) and
the [summary on typical comments during Go code
reviews](https://github.com/golang/go/wiki/CodeReviewComments).

Cover all new functionality with tests. Enable Travis on your forked repo,
enable builds of branches and make sure Travis is happily green for the branch
with your changes.

The code coverage is measured for each pull request. The code coverage is
expected to go up with every change.

Pull requests not meeting the above guidelines will get less attention than good
ones, so make sure your submissions are high quality.

# The small print

Contributions made by corporations are covered by a different agreement than the
one above, the [Software Grant and Corporate Contributor License
Agreement](https://cla.developers.google.com/about/google-corporate).

## Code Review Comments and Effective Go Guidelines
[CodeLingo](https://codelingo.io) automatically checks every pull request against the following guidelines from [Effective Go](https://golang.org/doc/effective_go.html).


## Single Method Interface Name
By convention, one-method interfaces are named by the method name plus an -er suffix 
or similar modification to construct an agent noun: Reader, Writer, Formatter, CloseNotifier etc.

There are a number of such names and it's productive to honor them and the function names they capture. 
Read, Write, Close, Flush, String and so on have canonical signatures and meanings. To avoid confusion, 
don't give your method one of those names unless it has the same signature and meaning. Conversely, 
if your type implements a method with the same meaning as a method on a well-known type, give it the 
same name and signature; call your string-converter method String not ToString.


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

