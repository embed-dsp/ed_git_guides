
# Local Basics

## Initialilze
```sh
# Initialize new repository
git init
```

## Add
```sh
# Add file for tracking or staging
git add <file>
```

## Status
```sh
# Get status
git status
```

## Diff
```sh
# Show changes between workspace and staged
git diff

# Show changes between staged and repository
git diff --cached

# Show changes between workspace and repository
git diff HEAD
```

## Undo
```sh
# Undo staging a file
git reset HEAD <file>

# Undo changes to a file
git checkout -- <file>

# Undo changes to all files
git reset --hard
```

## Commit
```sh
# Commit changes
git commit -m "..."

# Commit changes (files are staged automatically)
git commit -a -m "..."

# Change the last commit message ...
git commit --amend -m "..."
```

## Rename
```sh
# Rename/Move
git mv <from> <to>
```

## Remove
```sh
# Remove file from version control and from workspace
git rm <file>

# Remove file from version control without removing it from workspace
git rm --cached <file>
```
