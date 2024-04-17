# rclone-install
my rclone install steps


## Installation

#### Step 1
```
apt update -y && apt upgrade -y
apt install wget unzip screen fuse
```
#### Step 2

To install rclone on Linux/macOS/BSD systems, run:
```
sudo -v ; curl https://rclone.org/install.sh | sudo bash
```
For beta installation, run:
```
sudo -v ; curl https://rclone.org/install.sh | sudo bash -s beta
```

## Rclone config

Please visit https://rclone.org/drive/ to get deep and detailed explanation for all configuration.
```
rclone config
```
## Mount to local
```
mkdir -p /your/path
fusermount -qzu /your/path
```

Test in another Terminal:
```
rclone mount remote: /your/path --allow-other --allow-non-empty --vfs-cache-mode writes
```

when you get these error:
```
Fatal error: failed to mount FUSE fs: fusermount: exec: "fusermount3": executable file not found in $PATH
```

install fuse3 and try again
```
apt install fuse3
```

## Make it become service to start with system

To make rclone mount the remote drive even after rebooted the vps, create /usr/lib/systemd/system/rclone.service with following information:
```
nano /usr/lib/systemd/system/rclone.service
```
```
[Unit]
Description=rclone 

[Service]
User=root
ExecStart=/usr/bin/rclone mount remote: /your/path --allow-other --allow-non-empty --vfs-cache-mode writes
Restart=on-abort

 
[Install]
WantedBy=multi-user.target
```
### Start the service and enable service to start with system:
```
systemctl start rclone
systemctl enable rclone
```
