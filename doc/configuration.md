
# Configuration

## File Locations

```sh
--local
    .git/config
```

```sh
--global
    ~/.gitconfig
```

```sh
--system
    /etc/gitconfig
```

## List Configuration
```sh
# All.
git config --list

# Local.
git config --list --local

# Global.
git config --list --global

# System.
git config --list --system
```

## Basic Configuration
```sh
# User name & email address.
git config --global user.name "Gudmundur Bogason"
git config --global user.email gb@embed-dsp.com
```

```sh
# Default editor used for commit messages etc.
git config --global core.editor emacs
```

```sh
# On a Linux/Mac machine enable this to change CRLF to LF when commiting.
git config --global core.autocrlf input

# On a Windows machine enable this to get automatic conversion between CRLF and LF.
git config --global core.autocrlf true
```

```sh
# Cache credential information.
git config --global credential.helper cache
```

## Enable RCS Keywords

```sh
# Create RCS keyword filters and make them executeable
git_rcskw_clean.py
git_rcskw_smudge.py
```

```sh
# Place the RCS keyword filters in /home/gb/bin
```

```sh
# Tell git about the smudge and clean filters for RCS keywords
git config --global filter.rcskw.clean  /home/gb/bin/git_rcskw_clean.py
git config --global filter.rcskw.smudge /home/gb/bin/git_rcskw_smudge.py
```

```sh
# Update local .gitattributes file
.gitignore filter=rcskw
.gitattributes filter=rcskw
*.txt filter=rcskw
*.sh filter=rcskw
*.py filter=rcskw
*.m filter=rcskw
*.xml filter=rcskw
*.html filter=rcskw
*.java filter=rcskw
*.cs filter=rcskw
*.h filter=rcskw
*.c filter=rcskw
*.hpp filter=rcskw
*.cpp filter=rcskw
*.cxx filter=rcskw
*.asm filter=rcskw
*.v filter=rcskw
*.vhd filter=rcskw
```

```sh
# Place the following RCS kewords in the source files.
$Author:   $
$Date:     $
$Revision: $
```
