Environment Setup
======================

Prior to using Git to the fullest extent, several steps need to be completed.

## Create an SSH key

There are multiple methods in which one can communicate with remote repositories. The most common method is to utilize SSH keys and the SSH protocol. A SSH public/private key pair must first be created.

Create a new SSH key on your machine by executing the following command:

```
ssh-keygen -t rsa -b 4096 -C "your_email@exxonmobil.com"
```

_The proceeding command generates a new SSH key with 4096 bits of *type* RSA. Using an email address as the comment associated with the key pair is a common convention when utilizing SSH keys._

When you're prompted to "Enter a file in which to save the key," press [Enter]. This accepts the default file location.

Next, a prompt will appear where a passphrase can be associated to the SSH key. Instead of providing one, hit **enter** twice to accept a blank passphrase.

The key pair will be created in the home directory of the user in the `.ssh` folder. 

List the keys that were created in the prior command:

```
ls -l ~/.ssh/
total 8
-rw-------. 1 student student 3243 Sep  8 02:18 id_rsa
-rw-r--r--. 1 student student  745 Sep  8 02:18 id_rsa.pub
```

`id_rsa` is the private key and `id_rsa.pub` its the public key

## Configure Git

In the prior exercise, Git was installed using Ansible. Now, steps can be performed to customize the settings to denote the user executing commands, such as _Commits_. 

Each of these actions utilizes the `git config` command. Each repository contains a configuration file in the `.git/config` file that describes the configurations for the specific repository. Alternatively, configurations can be made at a global level where values are stored in a file located in `$HOME/.gitconfig`.

To avoid repeating for each repository, the following steps will be apply changes at a global level.

### Setting Your Email Address

Set the email address by executing the following command:

```
git config --global user.email "user@exxonmobil.com"
```

Confirm the email address was successfully set

```
git config --global user.email
user@exxonmobil.com
```

### Setting Your User Name

Git associates each commit with an identity. An identity can either be a first and last name or a username.

Execute the following command to set the username as your _First and Last name_

```
git config --global user.name "John Doe"
```

Confirm the username was successfully set

```
git config --global user.name
John Doe
```

View the resulting `.gitconfig` file that was modified as a result of the proceeding commands:

```
cat ~/.gitconfig 
[user]
	email = user@exxonmobil.com
	name = John Doe
```

## Add SSH Key to GitLab

Now that the steps necessary for creating and configuring SSH keys have been completed, the key can be added to GitLab. 

Navigate to GitLab, click your username at the top righthand corner of the page, and then select **Settings**. 

On the lefthand navigation bar, select **SSH Keys**.

GitLab will be configured with the previously generated public key and Git will utilize the private key to communicate with GitLab. The public key located at `~/.ssh/id_rsa.pub`. 

Copy the contents of this file into the _Key_ textarea and enter a name of your choosing in the _Title_ field if you would like to rename the default value provided.

```
cat ~/.ssh/id_rsa.pub
```

Once complete, click **Add Key** to add the SSH key to your account.

With the required configurations set, proceed to [Working with Git Repositories](../repositories/README.md)