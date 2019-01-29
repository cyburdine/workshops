Prerequisites
===============

This sections describes the steps that are required to support the Git workshop

## GitLab

[GitLab](https://gitlab.com) is the web based repository manager that is being used in this workshop. To support several of the exercises in this section, access to an account on the GitLab server must be available. 

First, open a web browser and navigate to [https://git.rhlabs.net](https://git.rhlabs.net)

Register for a new account by clicking the **Register** tab

Fill out the registration form, being sure to use your email address. Once complete, click the **Register** button. A confirmation will be sent to your email address. Complete the steps described in the email to activate your account. 

## Git

Git must be available on your workstation. While `yum` can be used to install the `git` package, we can use an ad-hoc Ansible command and the _[package]()_ module to install git.

Execute the following command to install git:

```
ansible localhost -c local -m package -a name=git
```

With all of the prerequisites complete, move on to [Setting Up Your Local Environment](../environment-setup/README.md)
