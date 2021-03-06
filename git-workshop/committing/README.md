Committing
=============

To illustrate how Git can be used to version files, let's go ahead and create a few files and show how Git tracks changes. 

## Creating A Commit

First, create a file called `README.md` and give it some content:

```
echo "# My First Git Repository" > ~/repos/hellogit/README.md
```

Use the `git status` command to show that Git detects the file. 

```
git status
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#	README.md
nothing added to commit but untracked files present (use "git add" to track)
```

Notice how the file is _untracked_. If you recall, git has multiple states for a given file: untracked, staged, committed.

Now, add the file to the staging area:

```
git add README.md
```

Run `git status` again

```
git status
# On branch master
#
# Initial commit
#
# Changes to be committed:
#   (use "git rm --cached <file>..." to unstage)
#
#	new file:   README.md
#
```

Now that the file is staged, it can be committed, thus versioning the file:

```
git commit -m "Added README"
[master (root-commit) 05fa82c] Added README
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
```

Every commit must have a commit message. It can be specified using the `-m` flag as indicated in the prior example, or omitted which will bring up a default editor where you can enter the message interactively. 

## Inspecting a Commit

All commits have a set of common properties:

* A Hash of the commit - a UUID
* The author
* Date and time
* Commit message
* Diff of the changes

The commit history can be displayed using the `git log` command.

```
git log
commit 05fa82cd74b765fd1c82d6f2727e0c14edff9654
Author: John Doe <user@myemail.com>
Date:   Sat Sep 8 06:26:13 2018 +0000

    Added README
```

Notice how the commit contains the username and email as specified in the global git configuration, date and time of the commit, and then the message.

## Making more changes

Lets make some changes by adding a description to the README.

```
echo -e "\nHello git repository" > ~/repos/hellogit/README.md
```

Run `git status`` again:

```
git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   README.md
#
no changes added to commit (use "git add" and/or "git commit -a")
```

Git can show the changes that have been made to files between commits using the `git diff` command:

```
git diff
diff --git a/README.md b/README.md
index a113924..b526539 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,2 @@
-# My First Git Repository
+
+Hello git repository
```

Add the README to the staging area

```
git add README.md
```

Changes can be unstaged using the `git reset` command:

```
git reset README.md
```

Finally, adding modified files to the staging area and committing them can be consolidated into a single command using the `-a` flag of the `git commit` command as shown below:

```
git commit -am "Added description of repository"
[master f680421] Added description of repository
 1 file changed, 2 insertions(+), 1 deletion(-)
```

Notice how a description of the change is printed including the number of lines that have been modified. 

The new commit can also be seen in the history using the `git log` command:

```
git log
commit f680421a102168d3efe7478304d05baf741d3bbf
Author: John Doe <user@myemail.com>
Date:   Sat Sep 8 07:17:57 2018 +0000

    Added description of repository

commit 05fa82cd74b765fd1c82d6f2727e0c14edff9654
Author: John Doe <user@myemail.com>
Date:   Sat Sep 8 06:26:13 2018 +0000

    Added README
```

With an understanding of how to commit files, the [next exercise](../branching-merging/README.md) will introduce branching as a mechanism to easily create features and merging which incorporates changes.




