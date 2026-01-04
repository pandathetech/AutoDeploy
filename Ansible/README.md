# Ansible

---

## Table of Contents
- [1. Install Ansible](#1-install-ansible)
- [2. Install Two Ansible Node Servers](#2-install-two-ansible-node-servers)
- [3. Create Two Host Groups](#3-create-two-host-groups)
- [4. Configure Passwordless SSH Authentication for Remote Hosts](#4-configure-passwordless-ssh-authentication-for-remote-hosts)
- [5. Create a Playbook to Install Apache Web Server on Ansible Clients](#5-create-a-playbook-to-install-apache-web-server-on-ansible-clients)
- [6. Install Git on the Ansible Controller](#6-install-git-on-the-ansible-controller)
- [7. Enable Git Tracking for Files in /etc/ansible](#7-enable-git-tracking-for-files-in-etcansible)

---

## My Network Infrastructure
To each of my three VMs created for my Ansible demo guide, I assigned a static IP address.

| Machine Name | IP Address   | Subnet Mask   | Gateway      |
| ------------ | ------------ | ------------- | ------------ |
| ansibleroot  | 192.168.20.2 | 255.255.255.0 | 192.168.20.1 |
| ansiblenode1 | 192.168.20.3 | 255.255.255.0 | 192.168.20.1 |
| ansiblenode2 | 192.168.20.4 | 255.255.255.0 | 192.168.20.1 |

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-01%20195543.png)

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20202309.png)

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20210233.png)

---

## 1. Install Ansible
I installed Ansible on an Ubuntu 22.04 VM.

```
sudo apt install ansible -y
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-01%20195706.png)

---

## 2. Install Two Ansible Node Servers
I created two other Ubuntu VMs and installed Ansible on them too.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20202522.png)

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20212105.png)

---

## 3. Create Two Host Groups
On my Ansible control node, I created a folder called `ansible` in the `/etc/` directory, then I edited the `hosts` file to insert two host groups.

```
cd /etc/
```

```
sudo mkdir ansible
```

```
cd ansible/
```

```
sudo vim hosts
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20214037.png)

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20214214.png)

---

## 4. Configure Passwordless SSH Authentication for Remote Hosts
On my Ansible control node, I generated an SSH key pair. Then I navigated to the `.ssh/` directory and confirmed the presence of these files: `id_rsa` and `id_rsa.pub`.

```
ssh-keygen
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20214321.png)

```
cd
```

```
cd .ssh/
```

```
ls
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20214504.png)

I viewed the contents of my RSA SSH key file. It is needed to be copied into the `authorized_keys` file of my two Ansible nodes.

```
cat id_rsa.pub
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20214554.png)

To establish SSH connections from my Ansible root VM to my Ansible nodes, I installed the OpenSSH server on all three of my VMs.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20215654.png)

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20215741.png)

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20215811.png)

In my two Ansible node machines, I created a `.ssh/` folder and created the `authorized_keys` file in it.

```
sudo mkdir -p ~/.ssh
```

```
cd .ssh/
```

```
sudo vim authorized_keys
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20220415.png)

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20220429.png)

I copied the contents of the `id_rsa.pub` file from my Ansible root machine and pasted them into the `authorized_keys` files of my two Ansible nodes.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20220536.png)

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20220602.png)

Now, from my Ansible control node (ansibleroot), I am able to connect to my two remote hosts via SSH without having to enter a password.

> Don't forget to enter `yes` when they ask you if you want to continue connecting.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20220838.png)

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20221018.png)

I ran the command `ansible all -m ping` from my Ansible control node to ensure they were accessible.

```
ansible all -m ping
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20221133.png)

To install the `emacs` and `lynx` software on each of my Ansible clients (nodes), I accessed the `/etc/ansible` directory and created a playbook named `install-emacs-lynx.yml` in my Ansible root VM.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20221401.png)

Here is a screenshot of my Ansible playbook for installing `emacs` and `lynx`.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Ansible/Assets/Screenshot%202026-01-02%20221851.png)

---

## 5. Create a Playbook to Install Apache Web Server on Ansible Clients
After creating a playbook to install the Apache server on my Ansible clients, I executed it using my `/etc/ansible/hosts` file. Here is a visualization of my Ansible playbook for this task.

![]()

![]()

To verify that the Apache server was installed on my two managed nodes, I accessed their default web pages using their public IP addresses.

![]()

![]()

---

## 6. Install Git on the Ansible Controller
I installed Git using the following command.

```
sudo apt install git -y
```

![]()

---

## 7. Enable Git Tracking for Files in /etc/ansible
To enable Git tracking of the files in the `/etc/ansible` directory, I initialized a Git repository, added the files to Git, and committed them.

```
sudo git init
```

```
sudo git add .
```

```
sudo git commit -m "[Your commit message]"
```

![]()

I also configured my user credentials (name and email).

```
git config --global user.name "[Your Name]"
```

```
git config --global user.email "[Your Email Address]"
```

![]()
