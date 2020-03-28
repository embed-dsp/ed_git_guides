
# Branches

## Show
```sh
# Show existing branches
git branch

# Show existing branches with the last commit
git branch -v

# Show local and remote branches
git branch -a
```

## Create & Checkout
```sh
# Create a branch
git branch br1

# Create and checkout a branch all in one
git checkout -b br1

# Checkout branch
git checkout br1
```

## Delete
```sh
# Delete local branch
git branch -d br1

# Delete local branch and force removal of commit if not referenced anymore
git branch -D br1

# Delete remote branch: remote/origin/br1
git push origin --delete br1
```

## Changes
```sh
# See what has changed between the current branch br1 and the master branch
git diff master

# See what has changed for the file foo.c between the branch br1 and the master branch
git diff br1 master -- foo.c
```

## Merging
```sh
# Merge br1 branch into master branch
git checkout master
git merge br1

# Merge a specific file foo.h from br1 branch into master branch
git checkout master
git checkout br1 foo.h

# Mark conflicting file as resolved
git add <file>

# Show which branches have been merged in
git branch --merged

# Show which branches have not been merged in
git branch --no-merged
```

## ...
```sh
# Copy file from one branch to another.
git show <branch>:path/to/file > path/to/file

# Copy file from one branch to another and add to index.
git checkout <branch> path/to/file
```
