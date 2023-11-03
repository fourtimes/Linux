#  Install NFS Server and Client on Ubuntu 22.04

### 1. Install NFS Kernel Server in Ubuntu

_Before we do nfs kernel installing, let's first update the system packages._
```
sudo apt update
```
_After update the packages, let's install the nfs-kernel-server_
```
sudo apt install nfs-kernel-server
```
_Create an NFS Export Directory_
```
sudo mkdir -p /mnt/nfs_share
```
Give the directory owner permission for the NFS Export Directory.The Permissions means, we want all the client machines to access the shared directory, remove any restrictions in the directory permissions.

```
sudo chown -R nobody:nogroup /mnt/nfs_share/
```
Here we have give privillages the specified directory
```sh
sudo chmod 777 /mnt/nfs_share/
```















Reference - https://www.tecmint.com/install-nfs-server-on-ubuntu/
