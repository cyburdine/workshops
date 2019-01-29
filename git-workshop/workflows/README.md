Git Workflows
==========

While there are no single standard, Git contains a number of recommended workflows methods for using the tool effectively. In this section, we will walk through one of the most common methods: The fork and pull model.

## Exercise Overview

The goal of this exercise is to demonstrate how to utilize the Fork and Pull workflow in terms of GitLab as each student makes a modification in a shared repository by first creating a copy of their own (fork) and making a contribution to the centralized repository. 

## Forking a Repository

The shared repository for this exercise is called [fork-pull-example](https://gitlab.xom.cloud/hackathons2018/fork-pull-example) and contains a basic ansible playbook that loops through a folder containing different events and the students in attendance. 

Navigate to the repository in GitLab. ```CLICK ON THE LINK ABOVE TO FORK``` from example.

Next, Fork the repository to create a copy your own namespace by clicking on the **Fork** button. If you are a member of multiple organizations, you may need to choose your username as the organization that you would like to fork the repository to.

After the fork was created, clone the repository locally to your machine by locating the URL at the center of the screen, ensuring _https_ is the protocol type and then copying the url. Execute the following command to clone your forked repository locally and change into the directory as shown below:

_Note:_ Make sure that you are no longer inside the hellogit directory. If you are, move one level up by running the `../` command

```
git clone git@gitlab.xom.cloud:<USER>/fork-pull-example.git
cd fork-pull-example
```

_Note_: Be sure that you are using the **SSH** reference to the repository instead of https

## Creating a Feature

To demonstrate how git workflows can be utilized effectively, we will walk through the steps of creating a file in the repository with the first letter of your first name and your last name (such as _ablock_).

Let's create a new feature for this task by creating a new branch called `feature/attendance`

```
git checkout -b feature/attendance
```

_Note: Recall `git checkout -b` creates a new branch and switches to the newly created branch_

Now, inside the repository, create a folder for your locale (for budapest use bp)

```
mkdir -p workshops/bp
```

Create a new file with the first letter of your first name and your last name. 

```
touch workshops/bp/[YOUR NAME]
```
replace [YOUR NAME] with first initial and last name

An Ansible playbook to execute the actions within the repository called _workshop_attendees.yml_ can be used to validate your work. Run the following command to execute the playbook:

```
ansible-playbook workshop_attendees.yml
```

The final play will display the attendees and their workshop location.  It will look something similar to the following:

```
TASK [Print out Workshop Attendees] *********************************************************************************************
ok: [localhost] => {
    "files": [
        "Workshop: bp - File: ablock"
    ]
}

PLAY RECAP **********************************************************************************************************************
localhost                  : ok=4    changed=0    unreachable=0    failed=0
```

Once the file has been created, add the file and create a new commit to the repository.

```
git commit -am "Created attendance record"
```

Push the branch to the remote repository

```
git push origin feature/attendance
```

Once the branch has been pushed to GitLab, you can view it in the web browser by hovering over the _repository_ link on the lefthand navigation bar and then selecting **Branches**

## Creating a Merge Request

One of the primary reasons for forking a repository is to be able to work independently from the source repository. Ultimately, you may want to contribute changes back to the upstream repository. In GitLab, this is called a _Merge Request_.

To create a new Merge Request, click on **Merge Requests** on the lefthand navigation bar. 

Click on the **New Merge Request** button to begin the process of creating a merge request

The resulting page is split into two sections: The _Source Branch_, or the location containing the changes to be introduced, and the _Target Branch_, or the destination of where the changes should be applied.

Fortunately, GitLab proactively provides an intuitive **Create Merge Request** button when a new branch is pushed to a forked repository to aid in streamlining the merge request process. Confirm the branch in the description matches the name of the branch that was pushed to the repository. 

Enter a description of the change, confirm the source and target branch and then click **Submit Merge Request**.

A notification will be sent to maintainers of the upstream project

## Incorporating Changes

One of the key goals of the fork and pull workflow is to be able to easily incorporate changes from other contributors. 

Thus far, we have created a feature branch as well as created a merge request to the upstream repository. 

When changes occur in the upstream repository, we would want to incorporate those back into the forked repository. Otherwise, the contents of the forked repository becomes stale.

The first action that we would want to do is to add a new _remote_ that references the upstream repository. We'll call the remote `upstream`. To add a remote, the URL of the repository must be known as it is a required parameter. 

Navigate to the [upstream repository](https://gitlab.xom.cloud/hackathons2018/fork-pull-example) in GitLab and copy the **SSH** based URL. Execute the following command to add the remote

```
git remote add upstream <url>
```

Finally, we can incorporate changes from the upstream master branch to our own local branch. Recall in the fork and pull model, the master branch is treated as the "source of truth". 

Check out the master branch:

```
git checkout master
```

Now, pull in changes from the upstream master branch

```
git pull upstream master
```

Any changes that may have been added since you last forked the repository will be incorporated into your local branch. To update your fork on GitLab, you can push the changes from your local repository to complete synchronizing the fork:

```
git push origin master
```

