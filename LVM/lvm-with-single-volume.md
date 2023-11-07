## Logical Volume  Manager(LVM) Partition in Linux

### `LVM Installation`

To install LVM on Ubuntu, Debian, and Linux Mint:
```sh
sudo apt install lvm2
```
To install LVM on CentOS, Fedora, AlmaLinux, and Red Hat:
```sh
 sudo dnf install lvm2
```

### `Create partitions`
```sh
fdisk -l
```
![image](https://github.com/fourtimes/linux/assets/91359308/bf6ba0e3-3412-436d-b0a6-a8a4b6c8e4b9)

Next, let’s partition the disk with `cfdisk`
```sh
cfdisk /dev/xvdg
```
![image](https://github.com/fourtimes/linux/assets/91359308/f408c16e-3377-42f5-af48-aa81803950a7)

Now, we can see the partition's list.
```sh
fdisk -l
```
![image](https://github.com/fourtimes/linux/assets/91359308/7e72d0f6-f69a-4626-8135-6ff63484b211)

### Create physical volumes
```sh
pvcreate /dev/xvdg1
pvcreate /dev/xvdg2
pvcreate /dev/xvdg3
```
![image](https://github.com/fourtimes/linux/assets/91359308/9b44769c-5235-41bc-b204-bc9087685f93)

Use the `pvdisplay` command to see information about all the physical volumes on your system, or specify a particular volume you wish to view details about.
```sh
pvdisplay
OR
pvdisplay /dev/xvdg1
```
![image](https://github.com/fourtimes/linux/assets/91359308/521e3f4a-09ab-4233-9d58-3b70796faf68)

### Create a virtual group
```sh
vgcreate my-vg-group /dev/xvdg1 /dev/xvdg2 /dev/xvdg3
```
![image](https://github.com/fourtimes/linux/assets/91359308/d4528b65-a18c-4fb3-a72f-80dd045292be)

Use the following command to display information about the virtual group(s).
```sh
vgdisplay
```
### Create logical volumes
```sh
lvcreate -L 400 -n vol01 my-vg-group
lvcreate -L 1000 -n vol02 my-vg-group
lvcreate -L 5G -n vol03 my-vg-group
```
![image](https://github.com/fourtimes/linux/assets/91359308/02617dfa-2457-4d2b-b65e-6f2f60f12e3b)

![image](https://github.com/fourtimes/linux/assets/91359308/c34445de-6753-4337-902c-22d24d6e9051)

Finally, we can use the lvdisplay command to see the logical volumes we’ve just created.

![image](https://github.com/fourtimes/linux/assets/91359308/25d4d09b-d878-4622-8557-c93da9a7e7e3)

### Create a filesystem on logical volumes
```sh
mkfs.ext4 -m 0 /dev/my-vg-group/vol01
mkfs.ext4 -m 0 /dev/my-vg-group/vol02
mkfs.ext4 -m 0 /dev/my-vg-group/vol03
```
![image](https://github.com/fourtimes/linux/assets/91359308/99e58424-e155-4f0d-bee9-6b5ea39db2cd)

### Edit fstab to automatically mount partitions
```sh
# nano /etc/fstab
/dev/my-vg-group/vol01    /folder1   ext4   defaults    0       2
/dev/my-vg-group/vol02    /folder2   ext4   defaults    0       2
/dev/my-vg-group/vol03    /folder3   ext4   defaults    0       2
```
 ![image](https://github.com/fourtimes/linux/assets/91359308/73cdbfc7-2275-47c7-a16a-12f1879e6e47)

 ### Mount logical volumes
 ```sh
# create dir
mkdir /folder1
mkdir /folder2
mkdir /folder3

# validating the mounted folder's
mount -a
```
![image](https://github.com/fourtimes/linux/assets/91359308/606a3467-2cc8-4a8c-ac97-6be4d9dfe4fe)
![image](https://github.com/fourtimes/linux/assets/91359308/46f465d8-70b5-4074-98d9-258702994a26)

### Extend a logical volume
```sh
lvextend -L +1G /dev/my-vg-group/vol01
```
![image](https://github.com/fourtimes/linux/assets/91359308/5c5df2e2-6e49-43a1-8b21-df9a374c87e9)

resize the filesystem with the following command.

```sh
resize2fs /dev/my-vg-group/vol01
```
![image](https://github.com/fourtimes/linux/assets/91359308/94ece04d-afcd-47d1-b55d-7c3a11a3a842)

check the resized details of the specified mount point.

![image](https://github.com/fourtimes/linux/assets/91359308/4f601c32-e865-4fa1-9bcd-841db82ae1eb)

### umount dir
```sh
umount /folder1
```
![image](https://github.com/fourtimes/linux/assets/91359308/f68abe99-f9f5-440f-a38f-a82ddd2db140)

### Remove a logical volume
```sh
lvremove /dev/my-vg-group/vol01
```
![image](https://github.com/fourtimes/linux/assets/91359308/192b9327-b792-4023-90ae-436fdcb1f9e1)

FINAL OUTPUT
-----------
![image](https://github.com/fourtimes/linux/assets/91359308/c0662408-aba4-4f2a-aabb-6eca3e23d8a3)
