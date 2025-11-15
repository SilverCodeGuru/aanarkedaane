# Packages

**APT** Advaced Package Tool. Package manager for ubuntu.

Ubuntu has many versions. Each version has a nick name. Following commands tell you the nichname for your version

```bash
lsb_release -c
```

![alt text](<lsbrelease -c output.png>)

.deb files are packages like .msi files on windows.

apt tool download versions from different repos (repositories)

mongosh is available from mongo repositories

before you add a new repository on your system, you should download and save GPG key for the repository.

```bash
curl -fsSL https://pgp.mongodb.com/server-6.0.asc | sudo gpg --dearmor -o /usr/share/keyrings/mongodb-server-6.0.gpg
```

then add the repo for the codename/nickname for the version of your distribution

```bash
echo "deb [ signed-by=/usr/share/keyrings/mongodb-server-6.0.gpg ] https://repo.mongodb.org/apt/ubuntu noble/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
```

now you run following command to update the list of available packages

```bash
sudo apt update
```

then you install using the following command

```bash
sudo apt install mongosh
```

this command might still fail as package might not be available for your version.

you can now try going back to older (and compatiable) version by adding repo for older version.

but even than might fail and in that case you need to download the .deb file provided and install it using apt install command

```bash
wget https://downloads.mongodb.com/compass/mongosh_2.2.4_amd64.deb
sudo apt install ./mongosh_2.2.4_amd64.deb
```
