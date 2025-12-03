# Linux Virtual Machine with Oracle Virtual Box

- there is no GPU support. To work with API, better use WSL
- creating a VM was a bit difficult. None of the instructions worked. iso file was needed for install.
- there is another guest iso that was needed for resolution fix else the VM screen was too small

# Installations
- curl
- pyenv (using script based on instructions)
- builessential and lot of other libraries
- python 3.12.12
- install poetry (using script based on instructions)
- set python 3.12.12 as global python
- install vs code 
    - first add microsoft gpg key
    - add microsoft repo
    - apt install code
- install git (apt)
- generate ssh key with passphrase
- register public ssh key with github as authentication key
- git clone command showed an SSH key for github server, verify by searching on internet
- asked to enter passphrase and then clone succeeded
- git glbal config setup
    - user.name
    - user.email
- commit and push succeeded without any issues
- its time to start building with AI