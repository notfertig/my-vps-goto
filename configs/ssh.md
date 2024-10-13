
# Generate SSH-Keygen:
```
ssh-keygen -t ed25519 -C "user@host or email"
```

# Send your key to your server with:
``` 
ssh-copy-id -i ~/.ssh/yourkey -p 22 username@serveradress
``` 
This will send your key to your remoteserver 

# Edit your _sshd_config_
1. to disable password entry go to the sshd_config file under /etc/ssh/ 
edit your sshd_config file like this:

- PasswordAuthentication no
- ChallengeResponseAuthentication no
- PubkeyAuthentication yes

3. Safe file
4. sudo systemctl restart ssh
5. don't close your terminal yet
6. open a new terminal an test your config, if its not working out comment the PasswodAuthentication No from step 5

# SSH config-file for easy access to your remote
create a new file with the name _config_ in the .ssh folder of your host and copy&paste the follow lines 

```
Host Hostname
    HostName IPAdress
    Port 22
    User Username
    IdentityFile ~/.ssh/yourprivatekey
```    
