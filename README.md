# fail2ban-docker-nginx
This repository has some example files to protect your docker (nginx) container using Fail2ban (0.11) running on your host. The files are basic examples, and these are just to show how you can protect the containers using Fail2ban.

## The scenario

A host (server) running Linux and a docker running Nginx. Actually, you can protect any container because the firewall
rules are created to the **DOCKER** chain of the Iptables.

## Requirements

Your container's log files must be accessible from the host OS, for this you can use [volumes from docker](https://docs.docker.com/storage/volumes/) (In the follow section, the example `jail.local` is using volumes from a Nginx container in the folder `/myvolume/nginx/log`. 

## Steps

1. Install Fail2ban on you server

2. Put the file `nginx-404.conf` in the folder `/etc/fail2ban/filter.d/`

3. Put the files `iptables-common-docker.conf`and `iptables-multiport-docker.conf` in the folder `/etc/fail2ban/action.d/`

4. Add this to your `jail.local` file, this file is usually in `/etc/fail2ban/` folder.

```
[nginx-404]
enabled = true
port     = http,https
name = nginx404
action = iptables-multiport-docker
filter = nginx-404
logpath = /myvolume/nginx/log/*access*.log
bantime = 1h
findtime = 1h
maxretry = 3
```

5. Restart the fail2ban service and enjoy! 
 
