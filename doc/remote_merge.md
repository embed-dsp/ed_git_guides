
# Merge Repository A into Repository B with History

```sh
# Enter repository B.
cd B

# Add ...
git remote add foo https://github.com/embed-dsp/A.git
```

```sh
# ...
git fetch foo

warning: no common commits
remote: Counting objects: 41, done.
remote: Compressing objects: 100% (31/31), done.
remote: Total 41 (delta 12), reused 38 (delta 9), pack-reused 0
Unpacking objects: 100% (41/41), done.
From https://github.com/embed-dsp/A
 * [new branch]      master     -> foo/master
```

```sh
# ...
git merge --allow-unrelated-histories foo/master

Auto-merging README.md
CONFLICT (add/add): Merge conflict in README.md
Auto-merging LICENSE
CONFLICT (add/add): Merge conflict in LICENSE
Automatic merge failed; fix conflicts and then commit the result.
```

```sh
# ...
edit README.md ...
edit LICENSE ...
```

```sh
# ...
git add README.md
git add LICENSE
```

```sh
# ...
git commit -m "Merged repo A into repo B."
```

```sh
# ...
git remote remove foo
```
