### # Generate public/private key pair
```
cd ~/.ssh
ssh-keygen -t rsa -b 4096 -m PEM #make sure the private key start with 'BEGIN RSA..' not 'BEGIN OPENSSH..'
chmod 700 ./id_rsa.*
```

### # Go to FTP server
```
ssh ftpServer@ip
cd .ssh
touch authorized_keys
chmod 700 authorized_keys
exit
```

### # Copy public ssh key to ftpServer server
```
ssh-copy-id -i id_rsa.pub ftpServer@ip
```

### # Disable password authentication from ssh configuration
```
sudo nano /etc/ssh/sshd_config
```

Find `PasswordAuthentication`, and change the value to `no`, so it will look like this:<br>
```
PasswordAuthentication no
```

Restart ssh<br>
```
sudo service ssh restart
````

Copy the private key to private folder for the project, and change the extension to `.pem`.<br>
Finally, add the private key path to node ssh sftp configuration and put the passphrase there.<br>
