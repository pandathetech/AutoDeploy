# Docker (Ubuntu 22.04)
Docker is a containerization platform that allows you to package applications and their dependencies into lightweight, portable containers. This guide walks through installing Docker on **Ubuntu 22.04**, enabling and managing the Docker service, downloading images, creating containers, and accessing containerized applications through a web interface. It is intended for users who want a straightforward, step-by-step setup using the command line.

---

## Table of Contents
- [1. Install Docker](#1-install-docker)
- [2. Enable and Start Docker](#2-enable-and-start-docker)
- [3. Download a Docker Image](#3-download-a-docker-image)
- [4. Create a Container from a Docker Image](#4-create-a-container-from-a-docker-image)
- [5. Access the Container's Web Interface](#5-access-the-containers-web-interface)

---

## 1. Install Docker
After updating your system with the `sudo apt update && sudo apt upgrade -y` command, install Docker with apt.

```
sudo apt install docker.io -y
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Docker/Assets/Screenshot%202025-12-02%20135224.png)

---

## 2. Enable and Start Docker
To enable the Docker service, run the following command:

```
sudo systemctl enable docker
```

To stop the Docker service, run the following command:

```
sudo systemctl enable docker
```

To check Docker's running status, run the following command:

```
sudo systemctl status docker
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Docker/Assets/Screenshot%202025-12-02%20135408.png)

> If you want to disable and stop the Docker service, run the `sudo systemctl disable docker` and `sudo systemctl stop docker` commands respectively, then check the new status of the Docker service again.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Docker/Assets/Screenshot%202025-12-02%20135509.png)

---

## 3. Download a Docker Image
To download a Docker image, run the following command:

```
sudo docker pull [image_name]
```

> Replace [image_name] with the actual name of the Docker image you want to download. For example, nginx.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Docker/Assets/Screenshot%202025-12-02%20140209.png)

---

## 4. Create a Container from a Docker Image
To create a container from a Docker image, run the following command:

```
sudo docker run --name [container_name] -d -p 8080:80 [image_name]
```

> Remember to replace the two variables in brackets with their actual names.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Docker/Assets/Screenshot%202025-12-02%20140348.png)

You can check the list of your Docker processes with the following command.

```
sudo docker ps -a
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Docker/Assets/Screenshot%202025-12-02%20140652.png)

---

## 5. Access the Container's Web Interface
On a web browser, enter the following URL in your search bar to see the default web page of your container.

```
http://127.0.0.1:8080
```

or 

```
http://localhost:8080
```

> In my demo, I downloaded a nginx image for my Docker container.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Docker/Assets/Screenshot%202025-12-02%20140819.png)

---
