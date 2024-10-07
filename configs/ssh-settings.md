
# Generate SSH-Keygen:
ssh-keygen -t ed25519 -C "user@host or email"

# creating a SSH config-file for easy access to your remote servers
create a new file with the name _config_ in the .ssh folder of your host and copy&paste the follow lines 

```
Host Hostname
    HostName IPAdress
    Port 22
    User Username
    IdentityFile ~/.ssh/yourprivatekey #optional for passwordless login follow the steps below
```    


1. connect with your remote server
2. go to the ".ssh" folder (not exist create with "mkdir .ssh")
3. typ in "touch authorized_keys"
4. paste the content of your publickey
5. to disable password entry go to the sshd_config file under /etc/ssh/ and delete the comment at the position PasswordAuthenticaion and set the varible to no 
6. sudo systemctl restart ssh
7. don't close your terminal yet
8. open a new terminal an test your config, if its not working out comment the PasswodAuthentication No from step 5



``` 
ssh-copy-id -i ~/.ssh/yourkey -p 22 username@serveradress
``` 
This will add automaticle yout key to your server 
