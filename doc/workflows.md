
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
