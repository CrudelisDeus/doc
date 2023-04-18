# SMB

## About SMB

SMB (Server Message Block) is a protocol for exchanging files and printers between computers on a local network.

SMB runs over TCP/IP and uses ports 139 and 445. It supports user authentication and data encryption for security.

## About samba

Samba is free software that provides the ability to share files and printers between devices on a network based on different operating systems. In particular, Samba allows Windows users to share files with Linux devices and other operating systems.

### Config SMB

install smb and samba smbclient.

```bash
sudo apt-get update
sudo apt-get install samba smbclient
```

Now let's set up a user in the ubuntu server, and disable ssh access for him.

```bash
sudo adduser test
passwd test
```

Disable ssh

!!!default_ssh_conf

    /etc/ssh/sshd_config

```bash
DenyUsers test
# Reboot service ssh
sudo service ssh restart
```

Let's start setting up samba. Create a folder, add permissions for all users and configure the smb.conf file.

```bash
mkdir /data && chmod -R 777 /data
```

!!!default_samba_conf

    /etc/samba/smb.conf

```bash
[test]
# name network dir
path=/data
readonly = no
# This is an option that determines if the
# user has read-only access to the folder.
# In this case, users will be able to write
# files and change the contents of the folder.
comment = Security Folder
# This is the folder comment that will be
# displayed in the file browser window on
# the client computer.
security = user
# This defines the security level for accessing
# the network folder. In this case, the security
# level is set to "user", which means that access
# to the folder will be controlled by user accounts.
valid users = test
writable=yes
# indicates that the folder you set up in
# Samba is writable by users who have the
# appropriate permissions.
client lanman auth=yes
# enables support for client authentication through
# the LanMan protocol, which is used to support
# older clients that do not support more
# modern authentication protocols.
client ntlmv2 auth=no
# disables the use of the NTLMv2 authentication
# protocol, which can be useful if you have older
# clients that do not support NTLMv2.
```

After saving the changes, add the user to the list of Samba users, and set the password that will be used to access the directory.

```bash
sudo smbpasswd -a test
```

Reboot samba service.

```bash
sudo service smbd restart
```