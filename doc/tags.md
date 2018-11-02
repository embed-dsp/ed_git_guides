
# Tags

```sh
# Create an annotated tag.
git tag -a 0.1.0 -m "..."

# Create an annotated tag for a specific commit.
git tag -a 0.1.0 -m "..." 521daff

# Delete tag.
git tag -d 0.1.0
```

```sh
# Show existing tags.
git tag

# Show all tags from release 1.0.*
git tag -l '1.0.*'

# Show tag details.
git show 0.1.0
```

```sh
# Checkout a specific tag.
git checkout 0.1.0
```

```sh
# Push all tags to remote repository.
git push --tags

# Push specific tag to remote repository.
git push origin 0.1.0

# Delete tag from remote repository.
git push origin :refs/tags/0.1.0
```

```sh
# Show the most recent tag that is reachable from a commit.
git describe --tags --always
```
