
# GitHub SSH Keys

## Local Computer

```sh
# Generate a new SSH key
ssh-keygen -t rsa -C "gb@embed-dsp.com"
```

```sh
# Add SSH key to the ssh-agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

## GitHub

```sh
# Add your SSH key to GitHub
https://github.com/settings/keys

New SSH key
  Title: kenny: gb@embed-dsp.com
  Key:   <paste in the content of ~/.ssh/id_rsa.pub>
```

```sh
# Test SSH connection with GitHub
ssh -T git@github.com
```
