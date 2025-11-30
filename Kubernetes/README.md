# Kubernetes Cluster Setup Lab

## Table of Contents
1. [Install a Kubernetes Cluster with One Master and Two Workers](#1-install-a-kubernetes-cluster-with-one-master-and-two-workers)
2. [Test Your Cluster by Deploying an Nginx Application](#2-test-your-cluster-by-deploying-an-nginx-application)

## 1. Install a Kubernetes Cluster with One Master and Two Workers
After creating three Ubuntu servers (1 master node and 2 worker nodes), I assigned each one a static IP address and connected to them via SSH from a Ubuntu client.

![]()

![]()

![]()

On each node, I set its hostname.

![]()

![]()

![]()

On each node, I modified the `/etc/hosts` file to add the three node entries.

![]()

![]()

![]()

On each node, I ran `swapoff` and used the `sed` command to disable swap.

![]()

![]()

![]()

On each node, I loaded the following kernel modules.

![]()

![]()

![]()

On each node, I set the following kernel parameters for Kubernetes using the `tee` command.

![]()

![]()

![]()

On each node, I reloaded the above changes.

![]()

![]()

![]()

On each node, I installed the `containerd` dependencies.

![]()

![]()

![]()

On each node, I enabled the Docker repository.

![]()

![]()

![]()

On each node, I updated the system and installed `containerd`.

![]()

![]()

![]()

On each node, I configured `containerd` to use `systemd` as the cgroup driver.

![]()

![]()

![]()

On each node, I restarted and enabled the `containerd` service.

![]()

![]()

![]()

On each node, I downloaded the public signing key and added the Kubernetes apt repository.

![]()

![]()

![]()

On each node, I updated the system and installed Kubernetes components such as `kubectl`, `kubelet`, and `kubeadm`.

![]()

![]()

![]()

On each node, I held the Kubernetes components (`kubectl`, `kubeadm`, `kubelet`) to prevent them from being automatically updated.

![]()

![]()

![]()

On the master node, I initialized a Kubernetes cluster.

![]()

![]()

To start interacting with the cluster, I ran the following commands on the master node.

![]()

On the master node, I displayed the cluster and node status.

![]()

On each worker node (worker 1 and worker 2), I used the `kubeadm join` command that was previously noted after initializing the master node.

![]()

![]()

![]()

I checked the status of my nodes from the master node using the `kubectl get nodes` command.

![]()

I installed the Calico network plugin from the master node.

![]()

I checked the status of the pods in the `kube-system` namespace from the master node.

![]()

I re-checked the status of my nodes.

![]()

## 2. Test Your Cluster by Deploying an Nginx Application
To test the Kubernetes installation, I tried to deploy an Nginx-based application and access it.

![]()

I checked the status of the Nginx deployment.

![]()

I exposed the deployment as a `NodePort`.

![]()

I ran the following commands to display the status of the service.

![]()

Using a Firefox web browser, I was able to access the Nginx sites on each of my three nodes using port `31422`.

![]()

![]()

![]()
