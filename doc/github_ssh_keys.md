
# GitHub SSH Keys

## List existing public Keys
```sh
# List all files in the .ssh directory
ls -l ~/.ssh

# Any existing public keys are stored in the files
id_rsa.pub
id_ecdsa.pub
id_ed25519.pub
```


## Generate ED25519 Key

### Local Computer

```sh
# Generate a new SSH key
ssh-keygen -t ed25519 -C "gb@embed-dsp.com"
```

```sh
# Start the ssh-agent in the background.
eval "$(ssh-agent -s)"
```

```sh
# Add SSH key to the ssh-agent
ssh-add ~/.ssh/id_ed25519
```

### GitHub

```sh
# Add your SSH key to GitHub
https://github.com/settings/keys

New SSH key
  Title: kenny: gb@embed-dsp.com
  Key:   <paste in the content of ~/.ssh/id_ed25519.pub>
```


## Generate RSA Key

### Local Computer

```sh
# Generate a new SSH key
ssh-keygen -t rsa -C "gb@embed-dsp.com"
```

```sh
# Start the ssh-agent in the background.
eval "$(ssh-agent -s)"
```

```sh
# Add SSH key to the ssh-agent
ssh-add ~/.ssh/id_rsa
```

### GitHub

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
