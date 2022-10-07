Source Control Managment also known as Version Control Management is how a team of developers manage changes to their code so as not to step on each others toes and provide a method of backing up the source code between changes. 

Git is one of the most popular SCM tools. When Git is tracking a directory for changes it refers to it as a **sorce code repository**. 

The first step to using GIT with your application developement is to initialize the respository: 

Then you need to configure GIT to tell it which files you want to track, either everything in the directory or particular files:

When you're done configuring which files to track, each time you make a change, GIT will create a new version of that file. GIT won't save a new version every time you save the file, only when you tell GIT that you're done and that is called a **commit**. You don't have to commit all the files at once either, you can specify which files you want to commit and which ones you want to place into the **staging area**. 

###### Installing GIT
The instructions for installing GIT are on the website: https://git-scm.com/download/linux

For installing on Ubuntu/Debian use: 

```
sudo apt install git
```

For CentOS/RHEL use:

```
sudo yum install git
```

To check the version of GIT installed use:

```
git version
```

To initialize a repository under your current directory run:

```
git init
```

When you initialize a directory using GIT a hidden folder is created called .git. It is in this folder that all the information for the repository is stored.

To check the status of a GIT repo, use:

```
git status
```

To add files to the repo that you want to track (by default it is all files in the directory), use:

```
git add <FILENAME>

OR

git add . ## This will add all the files in the directory
```

When you make changes to a file that is being tracked, the GIT status command will show that there are changes to files that have not been commited. 

To add the files to the staging area you need to use:

```
git add <FILENAME>
```

You will then see that all files are ready to be commited when you run the status command.

To commit changes use:

```
git commit -m "MESSAGE HERE"
```

You have to type a message to commit with the changes, if you don't then GIT will open a new text editor for you to record a message. You're supposed to record what changes you've made to the code in this message. 

#### Remote Repositories

The above all assumes you're working with a local repository. Typically when you're working as part of a team you're using a remote respository that everyone has access to. 

You can host the repository on your local network or on an external one. 

If you have multiple people making changes to the same file and attempting to push the same commits, GIT is smart enough to know how to merge them without causing an issue. 

If however, a change has been made to the same line of code in the same file by multiple people, a merge conflict arises and you will need to tell GIT which change is to be accepted.

When all the developers have finished pushing their changes to the code, they can pull the latest files from the repository to make sure they have the most up to date files. 

#### Installing a GIT Server

So if you're looking to setup a remote repository on your local network, you simply have to setup git the way you would normally, (sudo yum install git -y) and then you can use

```
git daemon
```

this will run GIT as a simple TCP server and is all that is really required if you're using a local network git repositroy. 

You can also use a public repository with something like GitHub or GitLab. These are free and you can install a privately hosted version of GItLab on your network as well. 

#### Making a remote repository on GitHub

First you need to make an account and all that fun stuff but afterwards, you need to create a new repository using the Web interface. 

Click the + button somewhere on the page, usually top-right. Then give the repository a name and a description. 

![[Pasted image 20220606071028.png]]

You can also choose to make the repository public or pirvate. If you make it public anyone can view your source code. 

So now you've create a remote repository and you need to sync it up on your local computer. 

You'll be provided with a URL for your remote repository:

![[Pasted image 20220606071324.png]]

Then you will need to tell your local repository that there is a remote respository that you would like to use. To do this, use:

```
git remote add <name> <URL>
```

The name does not have to be the same as that of the remote respository, this is just for our own reference. 

You can have multiple remote repositories using the same code base and when you push your changes you can specify which ones you pushing the changes to. Say for example you have your code hosted on both GitHub and GitLab. 

To upload your changes / files to your remote repository you need to use the push command:

```
git push <name> <branch>
```

Note: *the default branch is called the master*

Since this is the first time we're pushing our code and the master branch is not already present on the remote repository we need to add the -u switch as welll:

```
git push -u github master
```

Now all the code in the local respository is uploaded to the remote repository and is available on github. 

If you're trying to add a new user to have access to the remote respository, the must first download or **clone** the repository to their local system. To do this use:

```
git clone <URL>
```

If you clone a remote repository to your local system, the remote repo is automatically configured for them. 

Note: This will create a folder in your current directory with the name of the repository

To list your remote repositories use the:

```
git remote -v
```

You'll note that the name of the repository is origin followed by the URL of the remote repository. 

If I were to make changes to the repository and other users wanted to download my changes, they could use:

```
git pull
```

which will download just the changes, instead of the entire repository.

