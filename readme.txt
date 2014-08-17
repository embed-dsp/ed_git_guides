
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


--------------------------------
Clone an existing repository
--------------------------------
git clone <from> <to>

git clone https://github.com/gudme/embed-dsp.git


--------------------------------
Create a new component
--------------------------------
* Initialize new repository
git init

* Add new file
git add <file>

* Get status
git status

* Commit file
git commit 
git commit --amend

* ...
git log

* ...
git show

* ...
git diff

* Rename/Move
git mv ...

* Remove file from version control without removing it from workspace
git rm --cached <file>

* Push changes back to master branch in origin server
git push origin master

* Show information about origin server
git remote show origin

--------------------------------
Move component into server
--------------------------------
* Make a bare clone
git clone --bare foo foo.git

* Move into server
mv foo.git /mnt/data1/git
