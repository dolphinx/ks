![Git](https://git-scm.com/images/logo@2x.png "Git")

# Git Introduction

Git */ɡɪt/* is a free and open source **distributed** version control system designed to handle everything from small to very large projects with speed and efficiency.

Git was created by Linus Torvalds in 2005 for development of the Linux kernel, with other kernel developers contributing to its initial development. Git's design was inspired by BitKeeper and Monotone.

# [Git Internal](https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain)
## .git directory
+ **objects** directory stores all the content for your database.
+ **refs** directory stores pointers into commit objects in that data (branches).
+ **HEAD** file points to the branch you currently have checked out.
+ **index** file is where Git stores your staging area information.
+ *description* file is only used by the GitWeb program, so don’t worry about it.
+ *config* file contains your project-specific configuration options.
+ *info* directory keeps a global exclude file for ignored patterns that you don’t want to track in a .gitignore file.
+ *hooks* directory contains your client- or server-side hook scripts.

## Git Objects
Git is a content-addressable filesystem (a simple key-value data store).
### Key: SHA-1 hash
```
$ echo 'test content' > test.txt
$ git hash-object -w test.txt
d670460b4b4aece5915caf5c68d12f560a9fe3e4
```
### Value
 All the content is stored as tree and blob objects, with trees corresponding to UNIX directory entries and blobs corresponding more or less to inodes or file contents.
```
$ git cat-file -p d670460b4b4aece5915caf5c68d12f560a9fe3e4
test content
```
#### blob Objects

#### Tree Objects
print tree of master branch
```
$ git cat-file -p master^{tree}
100644 blob a906cb2a4a904a152e80877d4088654daad0c859      README
100644 blob 8f94139338f9404f26296befa88755fc2598c289      Rakefile
040000 tree 99f1a6d12cb4b6f19c8655fca46c3ecf317074e0      lib
```
print lib tree
```
$ git cat-file -p 99f1a6d12cb4b6f19c8655fca46c3ecf317074e0
100644 blob 47c6340d6459e05787f644c2447d2595f5d3a54b      simplegit.rb
```
![Tree](data-model-1.png "Tree")
#### Commit Objects
A commit specifies the top-level tree for the snapshot of the project at that point; the author/committer information (which uses your user.name and user.email configuration settings and a timestamp); a blank line, and then the commit message.

create a commit object
```
$ echo 'first commit' | git commit-tree d8329f
fdf4fc3344e67ab068f836878b6c4951e3b15f3d
```
print a commit object
```
$ git cat-file -p fdf4fc3
tree d8329fc1cc938780ffdd9f94e0d364e0ea74f579
author Scott Chacon <schacon@gmail.com> 1243040974 -0700
committer Scott Chacon <schacon@gmail.com> 1243040974 -0700

first commit
```
![Commit](data-model-3.png "Commit")

## Git References
### Head
A head is simply a reference to a commit object.

The HEAD file is a symbolic reference to the branch you’re currently on. 
```
$ cat .git/HEAD
ref: refs/heads/master
```
### Tags
Tags contains a tagger, a date, a message, and a pointer(point to a commit)

### Remotes
Read only

# Local operation
## Repository
### Create Repository
+ Make it Bare

### [Repository config](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration)
+ core.autocrlf true

Git can handle this by auto-converting CRLF line endings into LF when you add a file to the index, and vice versa when it checks out code onto your filesystem. If you’re on a Windows machine, set it to true – this converts LF endings into CRLF.

+ core.autocrlf input

If you’re on a Linux or Mac system that uses LF line endings, then you don’t want Git to automatically convert them when you check out files; however, if a file with CRLF endings accidentally gets introduced, then you may want Git to fix it. You can tell Git to convert CRLF to LF on commit but not the other way around.

+ core.autocrlf false

If you’re a Windows programmer doing a Windows-only project, then you can turn off this functionality, recording the carriage returns in the repository.

## Working Directory and Staging Area
![Life cycle](lifecycle.png 'Life cycle')
### File status
+ Modified
+ Added
+ Deleted
+ Missing
+ Unknown(Not Versioned)
### [Ignoring Files](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#_ignoring)
.gitignore
### Add
### Delete
### Commit
+ Ammend last commit
+ Revert(context menu)

**Check code changes before each commit**
### Diff
### Blame

## Branch
### Create Branch/Tag
### Delete Branch/Tag
### Export revision
### Browse revision
### Stash
### Switch/Checkout to
### Revert
+ Revert changes by commit
+ Revert files
### Compare revision
+ unified diff
### Merge to
+ Resolve conflicts and commit
### Combine commits
### [Rebase onto](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)
### Reset to
+ Mixed
+ Hard
### Bisect

## Reflog

## [Submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules)

# Remote operation
## Clone Repository
+ URL: local/UNC, https(smart/dumb), SSH, Git
+ From SVN

### Manage origin

## fetch
## pull = fetch + merge to remote
## push
+ Force known changes

## Misc
### [Diff Viewer & Merge Tool](http://www.scootersoftware.com/support.php?zz=kb_vcs#tortoisegit)