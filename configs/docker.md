# Install Docker and Docker Compose


Run install-docker.sh, to install docker, and add the current user to the docker usergroup.
```
wget -qO- https://raw.githubusercontent.com/notfertig/my-vps-goto/main/script/install_docker.sh | bash
```
You need to reboot/logout for changes to take effect


# Install Portainer

```
docker volume create portainer_data
```
```
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```


Logging In
> https://localhost:9443