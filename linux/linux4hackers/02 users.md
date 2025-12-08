# user management in linux

- only root can add users
- users are stored in /etc/passwd

```
thor:x:1001:1001:thor,,,:/home/thor:/bin/bash
```

- passwords are stored in /etc/shadow
- with sudo you can login with a password
- sudoers file
- not every user can become root 

## commands

- adduser - need to enter all information including password right away
- useradd - only adds user
- "sudo su -" -login as root
- sudo 
- ctrl+d - logout
- userdel
- usermod -aG allpowerful ironman - append ironman to allpowerful group
- sudo visudo
- visudo is a utility with syntax validation etc specifically for editing sudoers file