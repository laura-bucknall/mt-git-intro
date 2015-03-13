# Working with source control
# An introduction to Git

## Pre-requisites

This document assumes that;

* You have some understanding of what version control and/or Git is
* You have Git already installed (it is in K129)
* Git has been added to your PATH (i.e. you can execute *git* in a terminal/command prompt)

It will be helpful if you have;

* Some basic experience of working within a terminal or command prompt
* An account on a repository hosting service (details can be found later in this document)

## Preface

This document is intended as in introduction to working with source control using Git.

In order to be operating system, IDE and language agnostic, this document focusses on using Git from the terminal / command line.


* * *


## Git vocabulary

<table>
<th>
  <td>Term</td>
  <td>Definition</td>
</th>
<tr>
  <td>Repo / Repository</td>
  <td>Definition</td>
</tr>
<tr>
  <td>Public repo</td>
  <td>Definition</td>
</tr>
<tr>
  <td>Private repo</td>
  <td>Definition</td>
</tr>
<tr>
  <td>Push</td>
  <td>Definition</td>
</tr>
<tr>
  <td>Pull</td>
  <td>Definition.</td>
</tr>
<tr>
  <td>Pull request</td>
  <td>Definition</td>
</tr>
<tr>
  <td>Commit</td>
  <td>Definition</td>
</tr>
<tr>
  <td>Diff</td>
  <td>Definition</td>
</tr>
<tr>
  <td>Branch</td>
  <td>Definition</td>
</tr>
<tr>
  <td>Checkout</td>
  <td>Definition</td>
</tr>
<tr>
  <td>Fork</td>
  <td>Definition</td>
</tr>
<tr>
  <td>History / Commit log</td>
  <td>Definition</td>
</tr>
<tr>
  <td>Remote</td>
  <td>Definition</td>
</tr>
<tr>
  <td>origin</td>
  <td>Definition</td>
</tr>
<tr>
  <td>master</td>
  <td>Definition</td>
</tr>
<tr>
  <td>Untracked</td>
  <td>Definition</td>
</tr>
<tr>
  <td>Octocat</td>
  <td>Definition</td>
</tr>
</table>


* * *


## CAUTION

If you do not have any prior experience with Git then it is strongly recommended that you practice in a new directory with files that, in a worst case scenario, you are prepared to lose.

You are encouraged to read around the topic, which may involve trying and running Git commands that you are unfamiliar with.
THERE IS THE POSSIBILITY THAT YOU COULD IRREVERSIBLY DESTROY DATA CONTAINED WITH YOUR GIT REPOSITORY/DIRECTORY IF YOU DO NOT KNOW WHAT YOU ARE DOING.

Git is not a replacement for carrying out your own local backups, and you are encouraged to perform these frequently.

Do not commit files that contain any sensitive information (usernames, passwords, email addresses etc.) as public repositories and other members of your repository will be able to see them.


* * *


## Creating a local Git repository

Using the command prompt, ensure that you are in the directory/folder you wish to initialise as a Git repository:

    H:
    cd H:\my-new-git-project

Run the following command to initialise a new Git repository in the current directory (the period means use the current directory):

    git init .

If successful, your terminal should output something similar to the following:

> Initialized empty Git repository in [path to your Git repository]


### Configuring Git

When you commit changes to your repository, your name and email address are associated with these changes so that others know who the author is and who is responsible for them.

You need to tell Git your name and email address, but please note that if your repository is public then both of these pieces of information will also be made public.

Set your name with the following command:

    git config user.name "YOUR NAME"

Set your email address with the following command:

    git config user.email "YOUR EMAIL ADDRESS"


### Projects with existing source-code

If you have initialised your git repository inside a directory containing existing source code, then you may wish to commit all existing files/directories to your Git repository.

Add all untracked files to your Git repository (the period means add all files in the current directory):

    git add .

Commit the added files with a commit message of 'Initial commit' (the -m flag indicates that we wish to supply a message)

    git commit -m "Initial commit"


* * *


## Creating and committing new files

### Create a new file

In an editor/IDE of your choice, create a new file (PHP, JS, HTML or CSS) in the usual way within the directory our Git repository is initialised in. Add some text content to this file and ensure that it is saved.


### Check the status of your repository

You can use the *git status* command to determine the current state of your Git repository. With your command line open run the following command:

    git status

Amongst other information, you should notice the following line under "Untracked files:" in the output of the git status command:

> my_file.php

The above informs us that Git is aware of new file(s) in your project, but that they are not yet tracked by Git. When a file is not tracked; Git is not storing its own copy of the file, changes to the file are not versioned within Git and ultimately the file will not be pushed to any remote repositories when a git push is performed.

Use the git status command to check the status of your Git project as you make changes. It will highlight untracked, deleted files, uncommitted files, committed files with new changes, renamed files and more.

### Add and commit the new file

Use the git add command to add the new file to your Git repository (where my_file.php is the name of your new file):

    git add my_file.php

Commit the added file with a commit message of 'Adding a file to git repository' (the -m flag indicates that we wish to supply a message)

    git commit -m "Adding a file to git repository"

### Check the status of your repository

Use the *git status* command again to check the status of our repository. You should notice the following line in the output, which means that all changes are committed:

> nothing to commit, working directory clean


* * *


## Modifying existing files and committing changes

Update a file within your Git repository using a text editor / IDE of your choice.

Check the status of your Git repository using the *git status* command. You should see something similar to the following output underneath the file "Changes not staged for commit:"

> modified:   my_file.php

Git is telling us that one of our files have been modified, and as part of the output also informs us to use *git add* to add our changes to a commit.
Git add is used to add changes (in this case to a file) to a commit which could include additions (new files) and modifications (changes to content).

As you have done previously, add this file to your commit using *git add* and then commit the changes with a message using *git commit*.

You can check whether or not your changes have been successfully committed by running the *git status* command and looking for the following in the command's output:

> nothing to commit, working directory clean


### Deletions

The steps above are very similar for deleting files. So that you have a new file to delete, first repeat the steps for adding a new file.
Ensure that your new file is committed and that *git status* outputs "nothing to commit...".

Delete one of your committed files from your local filesystem.

Check the output of git status. You should see something similar to the following as part of the output under the line "Changes to be committed":

> deleted:    my_file.php

Can you identify which step we do not need to perform when deleting a file?



* * *


## Registering with "repository hosting service"

Whilst there are a number of uses for Git when working entirely locally, making use of a web-based repository hosting service brings a number of benefits.

A typical use case for a repository hosting service is for coordinating work in teams, where the service acts as a "central" authoritative copy of source code.
Individual team members can pull down the latest versions of the code, work offline and commit changes locally, and then push changes up at appropriate points to the central repository for other team members to have access too.

When working as an individual, repository hosting services provide an off-site point for backups and often also provide helpful web-based interfaces for browsing code, examining the differences between files from one commit to another and interrogating commit logs and making quick edits.

Both GitHub and Bitbucket are suggested as web-based Git repository hosting services and offer a very similar feature-set.


### Bitbucket

Bitbucket (https://bitbucket.org) offer free accounts with *unlimited public and private repositories* when you add and verify your university email address.

Signup to Bitbucket: https://bitbucket.org/account/signup/


### GitHub

GitHub (https://github.com) offer free accounts with unlimited public repositories and *up to five private repositories* when you add and verify your university email address.

GitHub also offer a free 'Student Developer Pack' which may or may not be of interest to you: https://education.github.com/pack

Signup to GitHub: https://github.com/join



* * *


## Working with repository hosting services

### Adding a new repository on GitHub/Bitbucket

Create a new repository on your repository hosting service of choice. Guides for GitHub and Bitbucket are listed below.

* GitHub: https://help.github.com/articles/creating-a-new-repository/
* Bitbucket: https://confluence.atlassian.com/display/BITBUCKET/Create+a+repository#Createarepository-CreatearepoonBitbucket


### Adding a remote origin to your local Git repository

In order to push code to your GitHub or Bitbucket repository, you first need to add them as "remote origins" to your local Git repository.

Browse to your repository page on GitHub or Bitbucket. You should find instructions that contain your remote origin.

* On GitHub this might be listed under "... or push an existing repository from the command line"
* On Bitbucket this might be listed under "I have an existing project"

You might be presented with the option to choose between an HTTPS or SSH version.
Due to the setup in the labs you should use the HTTPS version as it is the easiest to work with and requires no additional configuration.

For Github the command should look something like:

    git remote add origin https://github.com/your_username/your_repo_name.git

For Bitbucket the command should look something like:

    git remote add origin https://your_username@bitbucket.org/your_username/your_repo_name.git

With the remote added we then want to push all of our commits to the server. Execute the following command:

    git push -u origin master

'origin' in the above commands refers to the local reference for our remote origin (the remote repository). You could name this github or bitbucket, or production and staging (for testing within different environemtns) or anything else you desire.

Visit your repository hosting service provider's web interface and navigate to your repository page. You should find that your files and source code are listed on the page.

### Pulling changes

The Git command "git pull [remote] [branch]" (e.g. "git pull origin master") is used to pull new commits from a remote to your local Git repository.

The easiest way to see this in action is to use either GitHub or Bitbucket's online file editors.
Browse your source code and look for an 'edit' button, make a change and commit it using the online editor.
If you browse back to your repository commit history then you should see this change listed there.

With the change made online, in your terminal/command prompt run the following command to pull any new commits from the remote origin:

    git pull origin master

Now imagine that several other people within your team were making changes and committing them to source control throughout the day (rather than you making all of the changes).


### Explore

Explore the many other features of the web-based platforms (links can be found at the end of this document), including commit history, file diffs (comparisons of files between one commit and another to highlight changes) and author information.


* * *


## Help improve this document

Have u spotted a typo, spelling error, inaccuracy or think this document is missing a key aspect of Git? Read on to find out how you can fix and contribute, using Git of course!


### Forking projects

Forking is a feature of both GitHub and Bitbucket which provides a shortcut for taking another user's hosted Git repository and creating your own version.

Browse to the advertised Git repository URL on the service provider of your choice, and look for a 'Fork' button.

* A guide to forking on GitHub: https://help.github.com/articles/fork-a-repo/ (follow Step 2)
* A guide to forking on Bitbucket: https://confluence.atlassian.com/display/BITBUCKET/Forking+a+Repository#ForkingaRepository-HowtoForkaRepository (follow steps 1-5 under 'How to fork a repository')

You should now have a copy of the advertised Git repository files on your local machine, where 'origin' is your own copy of the Git repository.


### Make your changes to this document

The file within the repo is actually a markdown representation of the PDF that you are reading right now. For a brief introduction to markdown take a look at https://daringfireball.net/projects/markdown/basics.

Make any changes you wish to the file, and following the steps covered previously in this document commit your changes and then push these changes up to your own copy of the Git repository on GitHub/Bitbucket.

If you would like to preview the markdown document as a formatted PDF, you can use an online tool such as http://www.markdowntopdf.com.


### Create a 'Pull Request'

Having forked a repository, you can create a 'Pull Request' to the author of the original repository asking them to *git pull* the changes that you have made on your copy of the repository.
This is referred to as pushing changes back *upstream*.

If your pull request is accepted, then your changes to this document will be merged into the authoritative version of the document.
In some instances your pull request may be declined as it may be incomplete, errornous, or simply unwanted.
In the event that your pull request is declined you can still continue to develop on your own copy of the original repository.

* A guide to creating a pull request on GitHub: https://help.github.com/articles/using-pull-requests/ (we are only working on the master branch, so look for the green "Create pull request" button)
* A guide to creating a pull request on Bitbucket: https://confluence.atlassian.com/display/BITBUCKET/Fork+a+Repo,+Compare+Code,+and+Create+a+Pull+Request (Step 5)


* * *

## Resources / Further reading

* Try Git (interactive tutorial): https://try.github.io/
* GitHub guides: https://guides.github.com
* Getting started with Bitbucket: https://confluence.atlassian.com/display/BITBUCKET/Getting+started+with+Bitbucket
* .gitignore files:
* Git workflows: https://confluence.atlassian.com/display/BITBUCKET/Work+with+pull+requests
* GitHub flow: https://guides.github.com/introduction/flow/index.html