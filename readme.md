
# Configuration Files

## Location

```sh
--system
    /etc/gitconfig

--global
    ~/.gitconfig

--local
    .git/config
```

## Basic Configuration

```sh
git config --global user.name "Gudmundur Bogason"
git config --global user.email gb@embed-dsp.com
git config --global core.editor emacs
git config --global credential.helper cache

# On Linux/Mac systems enable this to change CRLF to LF when commiting
git config --global core.autocrlf input

# On Windows systems enable this to get automatic conversion between CRLF and LF
git config --global core.autocrlf true

# List the current configuration settings
git config --list

export GIT_EDITOR=...
```

## Enable RCS keywords

```sh
# Create RCS keyword filters and make them executeable
git_rcskw_clean.py
git_rcskw_smudge.py

# Place the RCS keyword filters in /home/gb/bin

# Tell git about the smudge and clean filters for RCS keywords
git config --global filter.rcskw.clean  /home/gb/bin/git_rcskw_clean.py
git config --global filter.rcskw.smudge /home/gb/bin/git_rcskw_smudge.py

# Update local .gitattributes file
.gitignore filter=rcskw
.gitattributes filter=rcskw
*.txt filter=rcskw
*.sh filter=rcskw
*.py filter=rcskw
*.m filter=rcskw
*.xml filter=rcskw
*.html filter=rcskw
*.java filter=rcskw
*.cs filter=rcskw
*.h filter=rcskw
*.c filter=rcskw
*.hpp filter=rcskw
*.cpp filter=rcskw
*.cxx filter=rcskw
*.asm filter=rcskw
*.v filter=rcskw
*.vhd filter=rcskw

# Place the following RCD kewords in the source files
$Author:   Gudmundur Bogason <gb@embed-dsp.com> $
$Date:     2015-06-03 11:55:47 +0200 $
$Revision: 55600e6 $
```


# Generate SSH Keys

## Local server

```sh
# Generate a new SSH key
ssh-keygen -t rsa -C "gb@192.168.0.100"

# Add your SSH key to kenny
scp /home/gb/.ssh/id_rsa.pub gb@192.168.0.100:/home/gb/.ssh/authorized_keys
```

## GitHub

```sh
# Generate a new SSH key
ssh-keygen -t rsa -C "gb@embed-dsp.com"

# Add your SSH key to GitHub
kenny ...

# Test everything out
ssh -T git@github.com
```


# Misc

```sh
# File State
Untracked           Newly created file
Tracked             git add ...
Modified            ...

# File Location
Working Directory   git checkout ...
Staging Area        git add ...
Repository          git commit ...

# ...
branch  => commit
tag     => commit

commit  => tree

tree    => tree
        => blob

blob

# Show file type from SHA-1 <hash>
git cat-file -t <hash>

# Show file size from SHA-1 <hash>
git cat-file -s <hash>

# Show file content from SHA-1 <hash>
git cat-file -p <hash>

git ls-files ...
```


# Local repository

```sh
# Initialize new repository
git init

# Add file for tracking or staging
git add <file>

# Show changes between workspace and staged
git diff

# Show changes between staged and repository
git diff --cached

# Show changes between workspace and repository
git diff HEAD

# Undo staging a file
git reset HEAD <file>

# Undo changes to a file
git checkout -- <file>

# Undo changes to all files
git reset --hard

# Commit changes
git commit -m "..."

# Commit changes (files are staged automatically)
git commit -a -m "..."

# Undo previous commit ...
git commit --amend -m "..."

# Rename/Move
git mv <from> <to>

# Remove file from version control and from workspace
git rm <file>

# Remove file from version control without removing it from workspace
git rm --cached <file>

# Get status
git status

# View commit history
git log

# View commit history in short form
git log --oneline

# View commit history in short form with HEAD, branch and tag decoration
git log --oneline --decorate

# View commit history in short form with HEAD, branch and tag decoration and branch graph
git log --oneline --decorate --graph

# View commit history with patch
git log -p

# ...
git show
```


# Branch

```sh
# Show existing branches
git branch

# Show existing branches with the last commit
git branch -v

# Create a branch
git branch br1

# Checkout branch
git checkout br1

# Create and checkout a branch all in one
git checkout -b br1

# See what has changed between the current branch br1 and the master branch
git diff master

# See what has changed for the file foo.c between the branch br1 and the master branch
git diff br1 master -- foo.c

# Merge br1 branch into master branch
git checkout master
git merge br1

# Merge a specific file foo.h from br1 branch into master branch
git checkout master
git checkout br1 foo.h

# Mark conflicting file as resolved
git add <file>

# Delete branch
git branch -d br1

# Delete branch and force removal of commit if not referenced anymore
git branch -D br1

# Show which branches have been merged in
git branch --merged

# Show which branches have not been merged in
git branch --no-merged
```


# Tag

```sh
# Show existing tags
git tag

# Show all tags from release rel_1.0.*
git tag -l 'rel_1.0.*'

# Create an annotated tag
git tag -a rel_0.1.0 -m "..."

# Delete tag
git tag -d rel_0.1.0

# Delete tag from remote repository
git push origin :refs/tags/rel_0.1.0

# Show tag details
git show rel_0.1.0

# Checkout a specific tag
git checkout rel_0.1.0

# Push tags to remote repository
git push --tags

# Show the most recent tag that is reachable from a commit
git describe --tags --always
```


# Patching

```sh
# Create a series of patches with all history for the git_* files and place in the folder ~/patches
git format-patch -o ~/patches --root git_*

# Applay a series of patches from the folder ~/patches
git am ~/patches/*

# Push the applaied patches to the origin/master branch
git push origin master
```


# Stash

```sh
# ...
git stash save

# ...
git stash pop
```


# Move project onto server

```sh
# Either create a bare project from scratch
git init --bare foo.git

# Or clone an existing project into a bare project
git clone --bare foo foo.git

# Move project onto server
mv foo.git /mnt/data1/git
```


# Remote repositories

```sh
# Clone an existing repository
git clone <from> <to>
git clone https://github.com/gudme/embed-dsp.git

# Show information about origin server
git remote show origin

# Show the remote repositories
git remote -v

# Fetch data from origin server
git fetch origin

# Push changes back to master branch in origin server
git push origin master

# Delete remote branch br1
git push origin :br1
```


# Workflows

## Master Branch

```sh
# Get the latest master branch
#git pull origin master

# add, remove, commit ... master branch

# Get upstream changes and rebase local changes
git pull --rebase origin master

# Check status to see conflicting files
git status

# Resolve conflicts by editing files

# Mark file as resolved
git add <file>

# Continue with the next file
git rebase --continue

# Push changes back to master branch in origin server
git push origin master
```

## Feature Branch

```sh
# Get the latest master branch
git pull origin master

# Create working branch from master
git checkout master

#git branch wrk
#git checkout wrk

git checkout -b wrk

# add, remove, commit ... working branch

# Get the latest master branch and rebase working branch
git pull origin master
git rebase master
git rebase -i master

#git fetch origin master
#git rebase origin/master
#git rebase -i origin/master

# Run regression tests etc.

# Merge working branch into master
git checkout master

git merge wrk
git merge --no-ff wrk

# Update master branch
git push origin master
```
