#  Install NFS Server and Client on Ubuntu 22.04
`FLOWCHART`
-----
![image](https://github.com/fourtimes/linux/assets/91359308/9c4852ec-5e94-48d1-91c6-e290a461b625)

`WORKFLOW`
------
|s. nO.|Server Details|IP|
|------|--------------|---|
|1.|NFS Server|192.168.1.105|
|2.|NFS Clinet Server 1|192.168.1.106|
|3.|NFS Clinet Server 2|192.168.1.107|
###  Install NFS Kernel Server in Ubuntu 

**_`NFS Server IP  - 192.168.1.105`_**

1. Before we do nfs kernel installing, let's first update the system packages.
```
sudo apt update
```
2. After update the packages, let's install the nfs-kernel-server
```sh
sudo apt install nfs-kernel-server
```
3. Create an NFS Export Directory
```
sudo mkdir -p /mnt/nfs_share
```
4. Give the directory owner permission for the NFS Export Directory.The Permissions means, we want all the client machines to access the shared directory, remove any restrictions in the directory permissions.

```
sudo chown -R nobody:nogroup /mnt/nfs_share/
```
5. Here we have given privillages to the  specified directory.
```sh
sudo chmod 777 /mnt/nfs_share/
```
6. Grant NFS Share Access to Client Systems
 we have allowed an entire subnet to have access to the NFS share.
```sh
# sudo vim /etc/exports

/mnt/nfs_share  192.168.1.0/24(rw,sync,no_subtree_check)    # 192.168.1.0/24 - ip address depends on your system networks.  
```

7. Export the NFS Share Directory
 ```sh
sudo exportfs -a
sudo systemctl restart nfs-kernel-server
```
8.  Allow NFS Access through the Firewall
```sh
sudo ufw allow from 192.168.43.0/24 to any port nfs
sudo ufw enable
sudo ufw status
```
_**Note:**_
- Suppose we are using EC2. The 8th step (firewall) is not mandatory. because we need to allow permission at the **security group** level.

### Install the NFS Client on the Client Server 1 & 2

**_`NFS Server IP  - 192.168.1.106, 192.168.1.107 `_**

1. Firstly let's check the connectivity of nfs server to nfs client each server
```sh
telnet 192.168.1.105 111
```
2. Install the NFS-Common Package each client server's
```
sudo apt update
sudo apt install nfs-common
sudo systemctl start nfs-common.service
```
3. Check the nfs server mount point in client server's
```sh
sudo showmount -e 192.168.5.105
```
4. Create an NFS Mount Point on Client
```sh
sudo mkdir -p /mnt/nfs_client
```
5. Mount NFS server mount dir on Client server's
```sh
sudo mount -t nfs 192.168.1.105:/mnt/nfs_share /mnt/nfs_client
```
6. Create the directory on Client server's mount path
```sh
cd /mnt/nfs_client
sudo touch file1.txt file2.txt file3.txt hi.me hello.me
ls -l /mnt/nfs_client
```
7. Check the NFS server mount directory and if the files exist and compared to the nfs client server's mount path too.
```sh
# 192.168.1.105
ls -l /mnt/nfs_share
```
OUTPUT
---------
This is the example output for nfs server and client server's

`NFS Client Server`

![image](https://github.com/fourtimes/linux/assets/91359308/97caf39a-b59c-473a-8c4e-7089cadb91fb)

`NFS Server` - check the **ashli.txt** file exist or not.

![image](https://github.com/fourtimes/linux/assets/91359308/20b9534e-613a-4687-ac0d-aab1ae11ac1b)


---

Reference - https://www.youtube.com/watch?v=XNefA6zh0h4
