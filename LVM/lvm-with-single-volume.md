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

Finally, we can use the lvdisplay command to see the logical volumes we’ve just created.
![image](https://github.com/fourtimes/linux/assets/91359308/25d4d09b-d878-4622-8557-c93da9a7e7e3)
