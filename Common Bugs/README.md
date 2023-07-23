### 1. Install and configure Kubeflow on a Kubernetes cluster
#### Bug 1: can not remove microk8s

```bash
 sudo snap remove microk8s --purge
```
-> error: cannot perform the following tasks:
- Remove data for snap "microk8s" (1120) (unlinkat /var/snap/microk8s/common/var/lib/kubelet: device or resource busy)
  
-> reason in systemctl is running service relate to microk8s

-> Solutions
```bash
systemctl status  /var/snap/microk8s/common/var/lib/kubelet
sudo systemctl stop  /var/snap/microk8s/common/var/lib/kubelet
sudo snap remove microk8s --purge
```

---
#### Bug 2: installed microk8s with snap, but can not find command "microk8s" after installed

```bash
kubectl version --short
```

-> Client Version and server version difference will => command "microk8s" after installed

-> Solutions: delele old microk8s and reinstall with same version

### 2. Faill to build or error (when kubectl apply)

- Remove old cluster and set up more resource


### 2. Faill to build or error (when kubectl apply)