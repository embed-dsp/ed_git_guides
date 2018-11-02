
# Stash

## List
```sh
# List the stash entries that you currently have.
git stash list
```

## Save
```sh
# Save your local modifications to a new stash entry 
# and roll them back to HEAD (in the working tree and in the index).
git stash save  # DEPRECATED

# Save your local modifications to a new stash entry 
# and roll them back to HEAD (in the working tree and in the index).
git stash push
```

## Remove
```sh
# Remove a single stashed state from the stash list and apply it on top of the 
# current working tree state, i.e., do the inverse operation of git stash save.
git stash pop

# Like pop, but do not remove the state from the stash list.
git stash apply

# ...
git stash drop
```
