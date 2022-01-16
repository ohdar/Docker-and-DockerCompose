# How to run Prometheus and Grafana using Docker Compose
### Docker Compose is used for running multiple containers as one service. If you have an application/ stack requiring different services, docker compose enables creating one file which would start all containers as one service and avoid the need to start them separately. It is also possible to start one service at a time with docker compose. Today, we are going to look at how to run Prometheus and Grafana using docker compose.
## Infrastructure Pre-Requisite
1.	Window 10 Client Machine
2.	Git Bash Installed in Windows 10
3.	Ubuntu Server 20.04 LTS VM in Proxmox / VirtualBox
 ⦁	Ram : 4GB
 ⦁	Virtual CPU : 2

## Install using the convenience script
```
⦁	curl -fsSL https://get.docker.com -o get-docker.sh
⦁	sudo sh get-docker.sh [refer docker installation video in this channel]
⦁	sudo systemctl status docker
⦁	$> sudo groupadd docker 
⦁	$> sudo usermod -aG docker $USER
```
## Install Docker-Compose on Linux systems
### Prerequisites
⦁	Docker Compose relies on Docker Engine for any meaningful work, so make sure you have Docker Engine installed.
⦁	On desktop systems like Docker Desktop for Mac and Windows, Docker Compose is included as part of those desktop installs.
⦁	On Linux systems, first install the Docker Engine for your OS as described on the Get Docker page, then come back here for instructions on installing Compose on Linux systems.

1.	Run this command to download the current stable release of Docker Compose:
```
sudo curl -L "<https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)>" -o /usr/local/bin/docker-compose
```
2.	Apply executable permissions to the binary:
```
sudo chmod +x /usr/local/bin/docker-compose
```
3.	Note: If the command docker-compose fails after installation, check your path. You can also create a symbolic link to /usr/bin or any other directory in your path.
```
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```
4.	Test the installation.
```
docker-compose --version
```
5.	Uninstallation: To uninstall Docker Compose if you installed using 
```
sudo rm /usr/local/bin/docker-compose
```

### Commands:
```
1.	sudo docker-compose -f docker-compose.yml up -d Install Prometheus and Grafana in with Docker-Compose. 
2.	docker stop stops one or more containers. docker stop mycontainer stops one container, while docker stop $(docker ps -a -q) stops all running containers.
3.	docker-compose down
```
### How do I stop and delete all containers in docker?
### Procedure
1.	Stop the container(s) using the following command: ``` docker-compose down. ```
3.	Delete all containers using the following command: ``` docker rm -f $(docker ps -a -q) ```
4.	Delete all volumes using the following command: ``` docker volume rm $(docker volume ls -q) ```

## Prune unused Docker objects
### **Prune images**
### The docker image prune command allows you to clean up unused images. By default, docker image prune only cleans up dangling images. A dangling image is one that is not tagged and is not referenced by any container. To remove dangling images:
```
docker image prune
```
### To remove all images which are not used by existing containers, use the -a flag:
```
docker image prune -a
```
### By default, you are prompted to continue. To bypass the prompt, use the -f or --force flag.
### You can limit which images are pruned using filtering expressions with the --filter flag. For example, to only consider images created more than 24 hours ago:
