+++
title= "Learnings of the Day 13/12"
date= '2023-12-13'
draft= 'false'
tags= ["learning", "git","github"]
categories= ["Git/Github"]
+++

# Git/Github Learning Summary

## Basics
- **Git:** Version control system created by Linus Torvalds in 2005.
- **Repository:** Tracks changes in a codebase and consists of commits (snapshots of files).
- **Branch:** An alternate history for code.
- **Merge:** Combines branches into a single codebase.

## Basic Context
- **unstaged** : before commiting it was in 'unstaged' has happen.
- **staged** : after commiting it was in 'staged' has happen.
- **branch**, helps to work on independenly of different modules that can be merge later.
- **origin** : origin is the remote and the name origin is the default or convention. after you clone, you can see your remote.
$ git remote
origin
- **master** : master is the branch in origin that you want to push your changes to. They both refer to what's on GitHub.
- **git status** : we are in which state either in staged or unstaged and untracked files.
- **git log** : displays history of commited messaegs, author with date/time.
- **stash** : stash if we edit before pull it will abort so 'git stash' helps helps to store it in stack then we can use it in  'git stash pop'.

### Commands
- `$ git init`: Initializes a repository.
- `$ git add .`: Adds changes to the staged area.
- `$ git commit -m "msg"`: Commits changes with a message.
- `$ git branch alternate-universe`: Creates a new branch.
- `$ git merge alternate-universe`: Merges branches.

## Install
- `$ git --version`: Checks Git version.
- `$ git config --list`: Shows configuration details.
- `$ git config --global username "set"`: Sets the username globally.
- `$ git config --global useremail "set@mail"`: Sets the user email globally.

## Staging
- `$ git reset .`: Removes changes from the staged area.
- `$ git status`: Inspects the repository status.
- `.gitignore`: Specifies files/folders to be ignored.

## Commits
- `$ git commit -m "message"`: Commits changes with a message.
- `$ git log`: Displays commit history.
- `$ git commit -a -m "Fix: typo"`: Adds and commits without explicit staging.

## Remote (Github)
- `$ git remote`: Shows remote repositories.
- `$ git remote add origin https:\\URL.com`: Adds a remote repository.
- `$ git remote -v`: Shows additional remote information.
- `$ git remote show origin`: Displays more details about the remote.

## Push
- `$ git push origin master -u`: Pushes changes to the remote repository.

## Merge
- `$ git fetch`: Fetches changes from the remote repository.
- `$ git merge origin/master`: Merges changes from the remote.

## Pull
- `$ git pull`: Fetches and merges changes.

## Clone
- `$ git clone https:\\url demofilename`: Clones a repository.

## Branch
- `$ git branch`: Lists branches.
- `$ git branch -M main`: Renames the master branch to main.
- `$ git branch awesome`: Creates a new branch.
- `$ git branch -d awesome`: Deletes a branch.

## Checkout
- `$ git checkout awesome`: Switches to the 'awesome' branch.
- `$ git checkout -`: Switches back to the previous branch.

## Conflicts
- Resolve conflicts when two branches modify the same code lines.

## Fork
- Creates a copy of the original code in your repository.

## Pull Request
- Contributes changes to the original repository via a pull request.

## Reset
- `$ git reset ID`: Resets the commit history.

## Revert
- `$ git revert ID`: Reverts changes and keeps commit history.

## Amend
- `$ git commit --amend -m "new message"`: Modifies the last commit.

## Stash
- `$ git stash`: Saves changes for later without committing.
- `$ git stash pop`: Applies stashed changes.

## Rebase
- Alternative to merge, keeps features in sync without extra merge commits.

## Squash
- Combines multiple commits into a single merge commit.

## Github Actions
- Automates workflows like CI, CD, npm publish, etc.

This summary covers the basic Git and Github commands and concepts, providing a structured overview for a beginner. Each topic is briefly explained, highlighting its importance for developers.







revision purpose for me:
```markdown
User
Today i learned Git/Github. I will abstract the command & topic what i learned, u might be  breifly explain its meanings y its used in situation like that and other important aspects need as developer. give in structured format of .md.

Basics:
git(Keep track of changes) : created by Linus Torvalds in 2005.
$git init : repository(tracks changes in codebase), commits(a snapshot of ur files)
$git add .
$git commit - m "msg" : head(most recent )
$git branch alternate-universe : branch(an alternate history for code)
$git merge alternate-universe : merge (combines branches into single codebase)

install:
git --version
git config --list : shows (username ,email ,etc)
git config --global username "set"
git config --global useremail "set@mail"
git init 

staging:
git add . : added to staged area(U->A)
git reset . : back to that(U<-A)
git add README.md
git status

status:
git status : for inspecting our repo(green color-new file, U-untracked,A-added to staged)
.git igonre : (to untract specific file/folder)

Commits:
git commit -m "message" : (changes made are color different)
git log : (commit references- author,id,date,etc..)(if changes made-shows in yellow color (M- modified))
git commit -a -m "Fix:typo" : this command add&commit without command of add.

remote (Github):
git remote (remote repo we linked to local project)
git remote add origin https:\\URL.com
git remote -v
git remote show origin :additional info

push:
git push origin master -u : origin is the name of repo, master is branch, -u is set to origin to upstream remote.

merge:
//still we have now 2branches in play
github(remote-master) && Vscode(local-master)
git fetch : to merge which is modified in github(download latest changes)
git branch 
git merge origin/master

pull:
git pull : fetch + merge (we cant use origin master because we used -u)
caution:- must have clear working directory

clone:
git clone https:\\url demofilename
git log

branch:
git branch
git branch -M main (rename master to main)
git branch awesome
git branch id awesome (deletes)

 checkout:
git checkout awesome : switvhed to 'awesome ' branch
git commit -am "added content"
git checkout - (back to previous branch)

conflicts:
if 2 branches modify the same code lines
git merge awesome (conflict aborts)
git commit -am "msg" (master merge)
git merge awesome (merge failed)
git diff (differece between 2 commits)
git merge --abort (back to original state)
//we can als commit both to resolve
git commit

fork:
Original code stored in our repo with upstream repo
then send pull request to merge code in original

pull request:
way to contribute
git branch
git checkout (switch)
//changes 
git add .
git commit 
git push origin (upload local changes to your remote repo)
//compare & pull req in github
//follow contri=buiton guideleinrs
git remote add upstream LINK
git fetch Upstream
git rebase upstream/master

reset:
3 different stykes of git is:1.working directory, 2. staging area, 3.commit history
git log (shows id-copy it)
git reset "ID"
// dont reset code on github after pushed.

revert:
git log
git revert "Id"
difference btwn these 2 are it still have commit history.

amend
git commit -am "bado" : typo in meesge,modify last commit (missing stage file) then
git commit --amend -m "bad"
or
git add.
git commit --amend --no-edit

Stash:
save ur work for later without commiting it.
git stash : array holds on changes apply it dates
git stash pop : put them backon code
git stash save post1
git stash save post2
git stash list : shows list of stashes 
git stash apply 1 : post1 shows.

rebase:
rebase vs merge 
//alternative to merge
keeps features in sync without extra merge commits

squash:
git commit -am "msg " : commits all into single merge
git rebase master --interactive : --interactive pulls up document in editor , replace pick->squash-> combine to single msg.
git log

github actions:
//automating workflows
1.CI
2.CD
3.Artifacts
4.npm publish
5.scheduled jobs


Thanks to fireship.<3
```
