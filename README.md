# Basic Git Commands

The readme is copied from https://github.com/quinnliu/<br/>
a simple video playlist on how to use Git & Github.com [here](https://www.youtube.com/playlist?list=PLPXsMt57rLtgpwFBqZq4QKxrD9Hhc_8L4&action_edit=1)

### Creating a repository online for the <b>1st time</b>!
``` sh
# navigated into your folder you want to put on Github
$ touch README.md # create a file called README.md where you can put instructions/info about your folder like what you are reading right now!
$ git init # initialize your git repository locally
$ git add . # adds everything changed from local to staging
$ git commit -m "first commit" # commits everything in staging to be ready to be pushed to Github
$ git remote add origin https://github.com/quinnliu/GitCommands.git
$ git push -u origin master # the "-u" is so that the next time your push you don't need to type "origin master"
# put in a username & password
```

### When adding on to your repository online with changes
``` sh
$ git add .
$ git add -u # when you have deleted a local file you want to remove from your repository
$ git commit -m 'what has changed'
$ git push 
# put in username & password
```

### No more username & password input for every push
``` sh   
# Note that you must first generate a SSH key on your local computer and add it to your 
# Github account before using the following command. Follow the directions here:
# https://help.github.com/articles/generating-ssh-keys
$ git remote set-url origin git@github.com:yourUsername/yourReponame.git
```

### Working together from perspective of person that doesn't have the main repo
``` sh
# fork repo you want to work on
$ git clone https://github.com/yourUsername/yourReponame.git
# add changes to your forked repo 
# make a pull request!
$ git pull # use this after someone else has made a change to the online repo 
           # your working on and you want to make your local repo up to date
```

### Remove directory from git and local
``` sh
# You could checkout 'master' with both directories;

$ git rm -r one-of-the-directories
$ git commit -m "Remove duplicated directory"
$ git push origin <your-git-branch> (typically 'master', but not always)
```
### Remove directory from git but NOT local
``` sh
# As mentioned in the comments, what you usually want to do is remove this directory from git but not delete it entirely from the filesystem (local). In that case use:

$ git rm -r --cached myFolder
```
### Commands for fixing problems
``` sh
# undo multiple commits  
$ git reset --hard commitSHA###... # changes staging index and 
                                   # local folder to match online 
                                   # repository commit

# removing 3 commits from online github repo
$ git push -f origin HEAD^^^:branchNameToUndoLast3Pushs
```

### Branch Commands 
``` sh
# creating a new branch
$ git branch -a # list all branches in working folder  
$ git branch newBranchName  
$ git checkout newBranchName # switch to branch newBranchName
$ git push -u origin newBranchName # adds new branch to github repo and "-u" lets 
#                                    you know when your local branch is different 
#                                    than the remote branch

# merging new branch to old branch
$ git checkout oldBranchName
$ git merge --no-ff newBranchName # "--no-ff" creates a commit that there was a branch merge
#                                   so in the future when you are looking at your commit log
#                                   you know when exactly when you merged one branch into another
$ git push origin oldBranchName 
$ git branch -D newBranchName # deletes local branch newBranchName
$ git push origin --delete newBranchName # deletes remote branch newBranchName
```
