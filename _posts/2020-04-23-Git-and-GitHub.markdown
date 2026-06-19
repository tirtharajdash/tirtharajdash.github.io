---
layout: distill
title: Git and GitHub (all you need)
date: 2020-04-23 04:00:00
description: What is Git, GitHub, and how do I get started?
authors:
  - name: Tirtharaj Dash
    url: "https://tirtharajdash.github.io/"
    affiliations:
      name: APPCAIR </br> BITS Pilani, Goa Campus
---
**What is Git?**

[Git](https://git-scm.com/) is a distributed version control system to effectively and efficiently track changes in source codes during the process of software development.


**What is GitHub?**

If you are reading this blog, then you must have heard about GitHub at least once. [GitHub](https://en.wikipedia.org/wiki/GitHub) (officially: GitHub, Inc.) is a US-based global company that provides hosting for software development version control. The version control is done with the help of **Git**. The company was [acquired by Microsoft](https://blogs.microsoft.com/blog/2018/10/26/microsoft-completes-github-acquisition/) in 2018. Since then, it has become a subsidiary of Microsoft.


By the way, **Who is the creator of these?**

Git was created by [Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds) in 2005 for development of the Linux kernel, with other kernel developers contributing to its initial development. GitHub was founded by Tom Preston-Werner, Chris Wanstrath, Scott Chacon, P. J. Hyett; all are software developers and entrepreneurs.


**Why should you bother about version control anyway?**

Version control in files, codes and other assets is a necessity as these things go numerous incarnations before become usable. There will be cases when overwriting a code can turn out to be a disaster leading to a total loss of all efforts. Manual version control is extremely cumbersome and sometimes may lead to content loss or unplanned commits. Automatic version control would help mitigate these problems, where you can just look at temporal changes made to the files and restore/accept the changes made recently. Further, the software is an outcome of effective collaboration of a team of contributors. Automated version control and collaboration tool such as GitHub allows these two very crucial operations. Therefore, it is imperative to know how to get our hands dirty with this tool.


**Requirements to get started**

Let's start. You need to have the following with you.

1. A machine (I mean, a computer system. I am using a Linux-based one.)
2. An account with GitHub. If you don't have one yet, create one for free here: [Join GitHub](https://github.com/join?source=header-home)
3. An editor installed in your machine. (I would prefer the simplest one. **vi editor**)


**Git installation**

Additionally, you need to check whether *git* is installed in your system. For this, open your terminal window (Ubuntu users: CTRL + ALT + T or right-click and "open terminal"), and type (don't include '$' in your command. This is just to show you that it is in terminal.)
```
$ git --version [ENTER]
```
If you already have *git* installed, it will show *git* version, which is in my case 2.17.1:
```
git version 2.17.1
```
You could also type *git* or *git --help* to get more information about the *git* commands.

If you do not have *git* installed in your system, then you need to install it (preferably, through the terminal). If you’re on Fedora (or any closely-related RPM-based distribution, such as RHEL or CentOS), you can use *dnf*:
```
$ sudo dnf install git-all
```
If you’re on a Debian-based distribution, such as Ubuntu, use *apt*:
```
$ sudo apt install git-all
```

After you are done installing *git*, verify your installation using the command mentioned earlier: *git --version*

If you reached to this point, you are ready to start. Let's start with setting up your *Git* account in your computer system.

Open a terminal/shell and type:
```
$ git config --global user.name "Your name here"
```
Set up the email ID (use the email ID associated with your GitHub account):
```
$ git config --global user.email "your_email@example.com" 
```
I also do:
```
$ git config --global color.ui true
```


#### **Step 0: Creating the first project repository**

It is convenient to use the browser to create a repository('repo' for short) under your GitHub account. Visit the [official help document](https://help.github.com/en/enterprise/2.14/user/articles/creating-a-new-repository) which is very well explained. However, make sure whether you want to make the repo *Private* or *Public*. As the word suggests, making a repo *Private* will make the repo inaccessible to others. Only the account owner can do modification to the repo.

Additionally, I would prefer to add a *README* along with the repo (the file will be stored as *README.md*; *.md* stands for *markdown language or extension*). This is nothing but a file that contains useful "readme" type information regarding the repo. 

Further, a *.gitignore* should also be added. This stands for a set of ignore rules. This allows you to list directories or files or extensions that should be ignored to be put into the online GitHub repo page. However, those ignored directories/files will sit inside your machine's work directories. For example, you have written a program that generates two temp files (*temp1.txt* and *temp2.txt*), and you think that this is not useful to be kept inside the repo: then you can ignore these two files by listing them inside *.gitignore* as:
```
temp*.txt
```

The next step starts the version control job. Just follow the following steps.


#### **Step 1: Cloning the repo into your system**

To get the repo as a directory inside your system, you need to *clone* it. Go to your preferable directory inside your system via your *terminal*. Now, navigate to the main page of the repository and follow the instruction to get the cloning link. The cloning link looks like the following:
```
https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
```
Let's use an exemplary name:
```
https://github.com/user.name/newrepo.git
```

Now, use the terminal to clone this into your system:
```
$ git clone https://github.com/user.name/newrepo.git
```
The terminal will show you the cloning outputs as follows:
```
> Cloning into `newrepo`...
> remote: Counting objects: 5, done.
> remote: Compressing objects: 100% (3/3), done.
> remove: Total 5 (delta 1), reused 5 (delta 1)
> Unpacking objects: 100% (5/5), done.
```
(The above is for demo purpose only.)


#### **Step 2: Work**

The above step will create a new directory named *newrepo* under your present working directory. You are free to treat this as any other directory and keep working. Happy coding!

If you think, you should post the new works back to the GitHub repo online; you can following the following steps.


#### **Step 2.1: Git status check (optional-yet-useful step)**

Additionally, you may want to check what are the new modifications done. 
```
git status
```


#### **Step 3 and 4: Add and commit changes**

You will use the add and commit functions to add and commit changes that you have made to your repo.

1. *git add*: It takes a modified file in your working directory and places the modified version in a staging area. The staging area is like an intermediate storage.
2. *git commit*: It takes everything from the staging area and makes a permanent snapshot of the current state of your repository that is associated with a unique identifier.

The overall process looks like this:
```
WORKING DIRECTORY ----(git add)----> STAGING AREA ----(git commit)----> GIT REPO
```

**Add files**

You have the flexibility to add a single file or a group of files to the staging area. To add a single file, use
```
$ git add <filename with extension>
```
For example:
```
$ git add README.md
```
To add all the files in your directory, use:
```
$ git add --all
```
Use git add --all with caution. You do not want to add things like credential files accidentally, .DS_Store files, or history files. Make sure these are included in the *.gitignore* rule.

**Commit files**

Once you are ready to create a snapshot of the current state of your repository, you can use git commit. The git commit command requires a commit message that describes the snapshot/changes that you made in that commit.

A commit message should be short and informative enough. This will help you as well as your collaborators or others. An example of a commit message is: *added new arguments to myfoo()*. Example of a commit command with a short message:
```
$ git commit -m "added new arguments to myfoo()"
```
Alternatively, if you want to explain your commits in multiline, you do so using an editor. 
```
$ git commit
```
This will use the default editor (in my case, *vi* or *nano*). If you prefer some other editor like *emacs*, you need to set it up for use by Git:
```
$ git config --global core.editor emacs
```
After you’ve made a few commits, check out the output of the git log command where you will be able to see the history of your repository, including all of the commit messages. This step is **optional**
```
$ git log
```

#### **Step 5: Now the BIG step (Pushing the repo online)**

You can push your changes to GitHub online account with:
```
$ git push
```
You will be prompted to enter the username and password of your GitHub account. Make sure that you enter those correctly. Don't worry if it gets typed wrong. It won't push. But, your commit is still there. So you need to type the command *git push again*.

This will show you all the stories that follow. After successfully pushed, you can check them online and you will feel happy. Welcome to the world of ***Git and GitHub***.


#### References

The following references were helpful while creating this article.

1. [Your fist time with Git and Github](https://kbroman.org/github_tutorial/pages/first_time.html) (accessed January 2020)
2. [First step with Git](https://www.earthdatascience.org/workshops/intro-version-control-git/basic-git-commands/) (accessed January 2020)

