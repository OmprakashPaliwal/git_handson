# git_handson
This repository is for git handson

tag histort :wqy

## clones a copy of git repo on your system
git clone <repo url> 
git clone https://github.com/OmprakashPaliwal/dev-ops-challenge.git


## .git folder
Contains git related configurations, Commits, history, branches, tags, user details, all the files that are part of git repo.

HEAD --- file points to latest commit


## Create a new branch
git branch <branch name>
git checkout <branch name>

### make changes
echo "This is feature a" > feature-a.txt
### check status of work dir
git status

### Add to stage area
git add <filepath>

### save changes
git commit -m "commit message"

### push local repo changes to remote repo
git push origin <branch name>

### to set remote branch and local branch connection,
git push --set-upstream origin feature-a

### see the new commit
git log

### get all git config
git config --list

location of the configs 
 .git/config
 ~/.git/gitconfig



## I want to get a file from feature-a branch to my branch
git checkout <commit/branch/tag> -- <filepath>
git checkout feature-a -- feature-a.txt


## How to get changes from orign branch to local branch (checked out)

git pull # brings changes from remote repository to local repository on the same branch (default)


## Feature C depends on feature B
git pull origin feature-b
git merge origin/feature-b


## Merging and working with Conflicts


                    team-A  --- changes automation.py|
                    |                                |
master              -- ---  ----- ------- ------   git merge team-a ----- conflict
automation.py       |                                                    |
                    team-B --- changes automation.py --------------------|


automation.py(team-a)

print("team a is good")

automation.py(team-b)

print("team b is good")

> git can't decide which line to keep. It if keep both than it will a duplication, if deletes teamb line, That will wipe out team b changes, or vice versa. 


how to resolve this

1. Accept the changes in HEAD (checkout branch)
2. Accept that is coming from remote commits. 
3. Accept both.  


Merge
git merge



Rebase
git rebase



Cherrypick
pick specific commit



### Merge - Combine branches
Assume the following history exists and the current branch is "master":

                     A---B---C topic
                    /
               D---E---F---G master

       Then "git merge topic" will replay the changes made on the topic branch since it diverged from master (i.e., E) until its current commit (C) on
       top of master, and record the result in a new commit along with the names of the two parent commits and a log message from the user describing
       the changes.

                     A---B---C topic
                    /         \
               D---E---F---G---H master
                            

### Rebase - Move a sequence of commits
Assume the following history exists and the current branch is "topic":

                     A---B---C topic
                    /
               D---E---F---G master

       From this point, the result of either of the following commands:

           git rebase master
           git rebase master topic

       would be:

                             A'--B'--C' topic
                            /
               D---E---F---G master
			   
