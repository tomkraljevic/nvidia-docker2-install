# nvidia-docker2-install
Shortcut instructions and binaries for installing nvidia-docker2.

## Summary

Installing nvidia-docker in an offline environment is tricky.  Here are some steps and canned artifacts to speed up the process.

The artifacts have been collected from open source Linux distributions using the standard package management tools.

---

## Platform x86_64-centos7

### Quick Start -- *This is all you need to do*

Step 1:  Install docker-ce.  This is a requirement for nvidia-docker2.

Step 2:  Download and install nvidia-docker2.

```
wget https://raw.githubusercontent.com/tomkraljevic/nvidia-docker2-install/master/x86_64-centos7.tar
tar xvf x86_64-centos7.tar
yum install x86_64-centos7/*.rpm
```

### Details about the tarball

Date created:  March 7, 2018

Contents:

```
-rw-r--r--  1 root root   32444 Mar  6 02:57 libnvidia-container-tools-1.0.0-0.1.beta.1.x86_64.rpm
-rw-r--r--  1 root root   72924 Mar  6 02:57 libnvidia-container1-1.0.0-0.1.beta.1.x86_64.rpm
-rw-r--r--  1 root root 2585528 Mar  3 01:50 nvidia-container-runtime-2.0.0-1.docker17.12.1.x86_64.rpm
-rw-r--r--  1 root root  630872 Mar  3 01:50 nvidia-container-runtime-hook-1.2.1-1.x86_64.rpm
-rw-r--r--  1 root root    4748 Mar  3 01:50 nvidia-docker2-2.0.3-1.docker17.12.1.ce.noarch.rpm
```

Assembly procedure:

```
yum install -y yum-utils device-mapper-persistent-data lvm2
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum install docker-ce
curl -s -L https://nvidia.github.io/nvidia-docker/centos7/x86_64/nvidia-docker.repo | tee /etc/yum.repos.d/nvidia-docker.rep
mkdir x86_64-centos7
yum install --downloadonly --downloaddir=x86_64-centos7 nvidia-docker2
tar cvf x86_64-centos7.tar x86_64-centos7
```
