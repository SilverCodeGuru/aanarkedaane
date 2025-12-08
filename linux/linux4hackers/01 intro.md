# Hackthebox VM

Github account
Parrot OS is based on Debian dsitribution

## Points

- linux is kernel that interacts with hardware
- linux is not OS
- different OS/distributions/flavors are built on top of linux kernel
- almost 600 distributions contains linux kernel
- GNU General Public License v2
- more secure, faster, open source
- less hardware drivers compared to windows
- today's terminal is terminal emulator - physical screen monitor keyboard
- shell is the UI - there are many shells e.g. bash, sh, zsh
- powershell also runs on linux - pwsh
- $ at command prompt means you are logged in as user
- su root will give you # instead of $
-



- everything is a file
  - all commands are files - lot of them are under /bin folder
  - all devices are also files

## Commands

- pwd
- cd
- ls
- clear (ctrl+l)
- whoami
- cat
- cp
- sudo
- rm
- which - find where command binaries live
- ctrl+c - cancel running command
- ps - proces status
- man - manual
- -h --help - help switch for every command
- apropos - search in existing commands



## root folders

### /bin

most commands are here

### /sbin

super bin
most admin (super essential) commands are here

### /usr

/usr/bin has same files as /bin. and so does sbin folder
it is same folder
i created kapil under  /bin and it is also under /usr/bin

something to do with space

/bin and /usr/bin are same directories

/usr/bin will have more files than /bin

/usr/local - newly created local binaries should be placed here

### /boot

boot files

### /root

root users folder

### /dev

dev stands for devices

- vda/sda - standands for disks (hard drives)

### /etc

place for configuration files
network/interfaces has network configuration

### /mnt

drives mounted manually

### /media

for USB