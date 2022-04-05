# fail2ban-docker-nginx
This repository has some example files to protect your docker (nginx) container using fail2ban runnin on your host. 

## The scenario

A host (server) running Linux and a docker running Nginx. Actually, you can protect any container because the firewall
rules are created to the **DOCKER** chain of the Iptables.


