# fail2ban-docker-nginx
This repository has some example files to protect your docker (nginx) container using Fail2ban (0.11) running on your host. The files are basic examples, and these are just to show how you can protect the containers using Fail2ban.

## The scenario

A host (server) running Linux and a docker running Nginx. Actually, you can protect any container because the firewall
rules are created to the **DOCKER** chain of the Iptables.


