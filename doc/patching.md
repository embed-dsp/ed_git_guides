
# Patching

```sh
# Create a series of patches with all history for the git_* files 
# and place in the folder ~/patches
git format-patch -o ~/patches --root git_*
```

```sh
# Applay a series of patches from the folder ~/patches
git am ~/patches/*
```

```sh
# Push the applaied patches to the origin/master branch.
git push origin master
```
