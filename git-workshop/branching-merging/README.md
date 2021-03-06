Branching and Merging
================

Branches are used to develop features isolated from each other. The default branch that is configured in each git repository is called `master` and this can be seen by executing the following command

```
$ git branch 
* master
```

The asterisk indicates that this is the branch that we are currently on. This will become more important shortly.

## Creating Branches

One of the best features of Git is the ease of managing branches. To demonstrate the how branches can be used, lets create a new branch called `feature` that will contain enhancements  to our existing repository. 

Creating branches in git is as easy as executing the following command:

```
$ git checkout -b feature
 Switched to a new branch 'feature'
```	

The _git checkout_ command is used to switch branches. The `-b` flag create a new branch and switches to the newly created branch. 

Alternatively, the combination of `git branch` and `git checkout` can be used to create new branches

```
$ git branch feature
$ git checkout feature
Switched to a  branch 'feature'
```	

If we execute the `git branch` command again, we can see that the pointer, represented by `HEAD`, is now next to the _feature_ branch.

```
$ git branch
* feature
  master
```

Switching back and forth between branches is easy:

```
$ git checkout master
Switched to branch 'master'
```

Now that we are back on the master branch, lets switch back to the `feature` branch

```
$ git checkout feature
Switched to branch 'feature'
```

## Making changes on the feature branch

To demonstrator the power and functionality of branching in git, let's create a new file called _file_. 

```
$ touch file
```

Add and commit the file to the repository 

```
$ git add file
$ git commit -m "Added file"
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file
```

## Merging 

Merging in git is a process where changes to the current branch are integrated from another branch. Features are typically short lived and are either abandoned or integrated. Let's go ahead and integrate the commit that was just made on the `feature` branch into the `master` branch.

First, checkout the `master` branch

```
$ git checkout master
Switched to branch 'master'
```

List the files in the directory and confirm _file_ is not present as it is on the `feature` branch and not on `master` which we are currently on

```
$ ls -l
total 4
-rw-r--r--. 1 student student 22 Sep  8 06:53 README.md
```

Merge the changes from the `feature` into the `mater` branch

```
$ git merge feature
Updating f680421..5d7bc73
Fast-forward
 file | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file
``` 

You may have noticed the term "fast-forward" in the output. This refers to the pointer for the branch moving forward to the new commit as no other divergent work needed to be managed. 

With an understanding of branching and merging, the next exercise will discuss sharing code to [remote repositories](../remotes/README.md) 