
Hello World! from wrk1

Copyright (c) 2013-2014 embed-dsp
All Rights Reserved

Author:  Gudmundur Bogason <gb@embed-dsp.com>
Created: 01-06-2014


* Configure
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

* ...
git log

* ...
git show

* ...
git diff

* Rename/Move
git mv ...

* Remove
git rm ...


--------------------------------
Move component into server
--------------------------------
* Make a bare clone
git clone --bare foo foo.git

* Move into server
mv foo.git /mnt/data1/git


--------------------------------
Clone an existing repository
--------------------------------
git clone <from> <to>


--------------------------------
Generating SSH Keys
--------------------------------
* Generate a new SSH key
ssh-keygen -t rsa -C "gb@embed-dsp.com"

* Add your SSH key to GitHub
kenny ...

* Test everything out
ssh -T git@github.com


--------------------------------
Caching your GitHub password in Git
--------------------------------
git config --global credential.helper cache


--------------------------------
Fork A Repo
--------------------------------
git clone https://github.com/gudme/embed-dsp.git


--------------------------------
Pushing to a remote
--------------------------------
git push origin master
