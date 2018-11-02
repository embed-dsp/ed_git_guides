
# Plumbing Commands

```sh
# Compute object ID from a file.
git hash-object <file>
```

```sh
# Return object ID.
git rev-parse <object>
```

```sh
# Show file type, size and content from <object>
git cat-file -t <object>
git cat-file -s <object>
git cat-file -p <object>
git cat-file commit <object>
git cat-file tree <object>
git cat-file blob <object>
```

```sh
# List the contents of a tree object.
git ls-tree <object>

# Show information about files in the index and the working tree.
git ls-files

# Show other (i.e. untracked) files.
git ls-files -o

# Show modified files.
git ls-files -m

# Show deleted files.
git ls-files -d

# Show only ignored files.
git ls-files -i
```
