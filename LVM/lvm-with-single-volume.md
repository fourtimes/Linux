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
cfdisk /dev
![image](https://github.com/fourtimes/linux/assets/91359308/f408c16e-3377-42f5-af48-aa81803950a7)

