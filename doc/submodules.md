
# Submodules

## Clone repository with submodules
```sh
# Clone a repository including all submodules.
git clone --recursive https://github.com/<user>/foo foo
```

## Update submodules
```sh
# Update all submodules.
git submodule update --init --recursive
```

## Add submodule
```sh
# Add a repository as submodule.
git submodule add https://github.com/<user>/bar bar
```

## Remove submodule
```sh
# Remove the submodule entry from .git/config
git submodule deinit -f bar

# Remove the submodule directory from the .git/modules directory.
rm -rf .git/modules/bar

# Remove the submodule directory.
rm -rf bar

# Remove the entry in .gitmodules
vim .gitmodules
```

## FIXME
```sh
# Show status for all submodules.
git submodule status --cached --recursive
```
