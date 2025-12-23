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

## 1. Install Ansible
First, I installed Ansible using `apt` on an Ubuntu 22.04 VM.

```
sudo apt install ansible -y
```

![]()

---

## 2. Install Two Ansible Node Servers
I created two other Ubuntu VMs and installed Ansible on them too.

![]()

![]()

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

![]()

![]()

---

## 4. Configure Passwordless SSH Authentication for Remote Hosts
On my Ansible control node, I generated an SSH key pair. Then I navigated to the `.ssh/` directory and confirmed the presence of three files: `authorized_keys`, `id_rsa`, and `id_rsa.pub`.

```
ssh-keygen
```

![]()

I ran the command `cat id_rsa.pub` to view the contents of my public key. I needed this to copy it into the `authorized_keys` file on my two other Ansible nodes.

```
cat id_rsa.pub
```

![]()

```
cd .ssh/
```

```
sudo vim authorized_keys
```

![]()

![]()

Now, from my Ansible control node, I was able to connect to my two remote hosts via SSH without having to enter a password.

![]()

![]()

I ran the command `ansible all -m ping` from my control node to ensure they were accessible.

```
ansible all -m ping
```

![]()

To install the `emacs` and `lynx` software on each of my managed nodes, I created a playbook in the `/etc/ansible` directory and executed it using my `hosts` file.

![]()

Here is the content of my Ansible playbook for installing `emacs` and `lynx`.

![]()

---

## 5. Create a Playbook to Install Apache Web Server on Ansible Clients
After creating a playbook to install the Apache server on my Ansible clients, I executed it using my `/etc/ansible/hosts` file. Here is the content of my Ansible playbook for this task.

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
