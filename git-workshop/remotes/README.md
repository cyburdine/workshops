Remotes
============

Git as a distributed version control system embraces the ability to utilize share versions of your repository on the internet. In this exercise, we will demonstrate how to make use of repositories that are hosted outside of your workstation.

## Creating a Repository on GitLab

Earlier in the workshop, we created an account on the GitLab sever. Now, let's use this access to create a new Project to share the _hellogit_ repository that we have been working on.

First, navigate to GitLab: [https://git.rhlabs.net](https://git.rhlabs.net) and login using the account created previously.

A project in GitLab is a space to host your codebase as well as features a number of collaboration tools including issue tracking, wiki and continuous integration and continuous delivery features.

Create a new project by clicking the **New Project** button.

Leave project path as the default and enter **hellogit** as the _Project Name_.

Enter an optional description if desired

Click **Create Project** to create the new project in GitLab.

## Adding a new remote and pushing code

Once a project has been created in GitLab, it can be referenced as a _remote_ within your local repository. Remotes are managed using the `git remote` command.

On the project details page, when no content exists within the repository, instructions are presented on how content can be added. Since a local repository already exists, the steps illustrated underneath the _Existing Folder_ can be used.

Add the GitLab repository as a remote being sure to replace the name of the repository specified by the `<USER>` value:

```
git remote add origin git@git.rhlabs.net:<USER>/hellogit.git
```

the new remote can be confirmed by listing the configured remotes for the repository as shown below. The `-v` flag provides additional detail including the URL of the repository.

```
$ git remote -v
origin	git@git.rhlabs.net:<USER/hellogit.git (fetch)
origin	git@git.rhlabs.net:<USER>/hellogit.git (push)
```

`origin` is the name of the default remote that git configures.

To update the remote repository with contents of the local repository, the `git push` command is used. When invoking the `git push` command, the name of the _remote_ and the _branch_ that should be updated on the remote repository can be specified.

Execute the following to update the GitLab repository:

```
$ git push origin master
Counting objects: 9, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (9/9), 730 bytes | 0 bytes/s, done.
Total 9 (delta 0), reused 0 (delta 0)
remote:
remote: ========================================================================
remote:
remote:    Gitlab does automatic patching and updating around 4:30 AM (UTC).
remote:         These updates may interrupt service briefly. Please plan
remote:                               accordingly.
remote:
remote: ========================================================================
To git@git.rhlabs.net:<USER>/hellogit.git
 * [new branch]      master -> master
```

Navigate back to the GitLab repository which should now contain the content from the local repository.

The final section describes how to utilize [Git Workflows](../workflows/README.md) during everyday development.
