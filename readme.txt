
Copyright (c) 2013-2014 embed-dsp
All Rights Reserved

Author:  Gudmundur Bogason <gb@embed-dsp.com>
Created: 01-06-2014


--------------------------------
Configure
--------------------------------
export GIT_EDITOR=...

--system
    /etc/gitconfig

--global
    ~/.gitconfig

--local
    .git/config

git config --global user.name "Gudmundur Bogason"
git config --global user.email gb@embed-dsp.com
git config --global core.editor emacs
git config --global credential.helper cache


--------------------------------
Generating SSH Key for GitHub
--------------------------------
* Generate a new SSH key
ssh-keygen -t rsa -C "gb@embed-dsp.com"

* Add your SSH key to GitHub
kenny ...

* Test everything out
ssh -T git@github.com

Hello

--------------------------------
Local repository
--------------------------------
* Initialize new repository
git init

* Get status
git status

* View commit history
git log
git log -p

* ...
git show

* Show changes between workspace and staged
git diff

* Show changes between staged and repository
git diff --cached

* Add file for tracking or staging
git add <file>

* Undo staging a file
git reset HEAD <file>

* Undo changes to a file
git checkout -- <file>

* Commit changes (files are staged automatically)
git commit -a -m "..."

* Undo previous commit ...
git commit --amend

* Rename/Move
git mv <from> <to>

* Remove file from version control without removing it from workspace
git rm --cached <file>


--------------------------------
Stash
--------------------------------
* ...
git stash save

* ...
git stash pop


--------------------------------
Branch
--------------------------------
* Show existing branches
git branch
git branch -v

* Create a branch
git branch br1

* Checkout branch
git checkout br1

* Create and checkout a branch all in one
git checkout -b br1

* Merge br1 branch into master branch
git checkout master
git merge br1

* Mark conflicting file as resolved
git add <file>

* Delete branch
git branch -d br1

* Show which branches have been merged in
git branch --merged

* Show which branches have not been merged in
git branch --no-merged


--------------------------------
Tag
--------------------------------
* Show existing tags
git tag

* Create an annotated tag
git tag -a rel_0.1.0 -m "..."

* Show tag details
git show rel_0.1.0


--------------------------------
Remote repositories
--------------------------------
* Clone an existing repository
git clone <from> <to>
git clone https://github.com/gudme/embed-dsp.git

* Show information about origin server
git remote show origin

* Show the remote repositories
git remote -v

* Fetch data from origin server
git fetch origin

* Push changes back to master branch in origin server
git push origin master

* Delete remote branch br1
git push origin :br1


--------------------------------
Move component into server
--------------------------------
* Create a bare repository
git init --bare /mnt/data1/git/test2.git

* Make a bare clone
git clone --bare foo foo.git

* Move into server
mv foo.git /mnt/data1/git
