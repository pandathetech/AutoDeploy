# Vagrant
My Vagrant guide provides a step-by-step introduction to Vagrant and explains how to set it up for creating virtual development environments. It is designed for beginners who want a simple and reliable way to manage virtual machines using code. By following this guide, you will learn how to install Vagrant, configure a basic `Vagrantfile`, and start your first virtual machine.

---

## Table of Contents
- [1. Install Vagrant](#1-install-vagrant)
- [2. Deploy Virtual Machines with Vagrant](#2-deploy-virtual-machines-with-vagrant)
- [3. Login to the Virtual Machines](#3-login-to-the-virtual-machines)
- [4. Vagrant Suspend](#4-vagrant-suspend)
- [5. Vagrant Halt](#5-vagrant-halt)
- [6. Vagrant Destroy](#6-vagrant-destroy)

---

## 1. Install Vagrant
*In my tutorial, I installed Vagrant in Windows 11.

In the search bar of a web browser, look up `vagrant` and click the `Install` option.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-30%20123704.png)

In the `Operating Systems` section, click `Windows`. Download the `AMD64` installer package.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-30%20124200.png)

After your installer package is done downloading, run the installer.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-30%20124823.png)

Accept the terms in the License Agreement. Click `Install`.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-30%20134215.png)

Once the setup is completed, click `Finish`.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-30%20135225.png)

Restart your Windows system to apply the configuration changes for Vagrant (Click `Yes`).

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-30%20135239.png)

---

## 2. Deploy Virtual Machines with Vagrant
Open a Command Prompt terminal and create a folder to initialize Vagrant. In the folder, you must have a Vagrantfile too.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-27%20141744.png)

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-27%20141819.png)

To provision a virtual machine with Vagrant, run the following command.

```
vagrant up [virtual_machine_name]
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-27%20143657.png)

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-27%20151244.png)

> If you want to provision all VMs mentioned in your Vagrantfile all at once, execute the `vagrant up` command.

In your hypervisor (for example, VirtualBox), verify that your VMs are created with Vagrant.

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-27%20151324.png)

---

## 3. Login to the Virtual Machines
To login to your Vagrant VMs, enter the required credentials.

- **Username** : vagrant
- **Password** : vagrant

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-27%20214011.png)

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-27%20215516.png)

---

## 4. Vagrant Suspend
By suspending a Vagrant VM, you pause its execution and save the state of the VM. To do so, you could either do:

- Suspend all running VMs

```
vagrant suspend
```

- Suspend a specified running VM

```
vagrant suspend [virtual_machine_name]
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-27%20215701.png)

---

## 5. Vagrant Halt
By halting a Vagrant VM, you stop its execution and don't save the state of the VM. To do so, you could either do:

- Halt all running VMs

```
vagrant halt
```

- Halt a specified running VM

```
vagrant halt [virtual_machine_name]
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-27%20215907.png)

---

## 6. Vagrant Destroy
By destroying a Vagrant VM, you delete everything related to it (configuration files, the VM itself, etc.). To do so, you could either do:

- Destroy all running VMs

```
vagrant destroy
```

- Destroy a specified running VM

```
vagrant destroy [virtual_machine_name]
```

![](https://github.com/pandathetech/AutoDeploy/blob/main/Vagrant/Assets/Screenshot%202025-11-27%20220029.png)

---

## 7. References
- [Vagrant's Official Website](https://developer.hashicorp.com/vagrant)
- [Discover Vagrant Boxes](https://portal.cloud.hashicorp.com/vagrant/discover)
- [Video Tutorial](https://youtu.be/sr9pUpSAexE?si=hyAAsIJNhX6jOmDt)
