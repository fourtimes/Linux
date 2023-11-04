# Logical Volume Manager (LVM):- [EC2]

1. Create a EC2 Instance.
2. Add a extra 2 Volumes in that specified Instance.
3. After that, we need to implement the LVM concept on those volumes.
4. Firstly, let's check the volumes.
```sh
sudo -i
lsblk
```
![image](https://github.com/fourtimes/linux/assets/91359308/9252b09b-b25f-4592-b501-cfa73eeae60d)

5. Then, We need to convert to physical volumes.
```sh
pvcreate /dev/xvdf /dev/xvdg
```
![image](https://github.com/fourtimes/linux/assets/91359308/ba9dc986-4c1f-415e-b79e-7e97ad182671)

6. List the PVS Details
```sh
pvs                     # Display information about physical volumes
pvscan                  # List all physical volumes
pvdisplay               # Display various attributes of physical volume(s)
```
![image](https://github.com/fourtimes/linux/assets/91359308/cdb66f77-82c6-47f0-92af-5a9b1f11bd78)
7. Next, Create a volume group.
```sh
vgcreate myvg /dev/xvdf /dev/xvdg              # myvg - as your wish to put volume group.
```
8. Display information about volume group.
```sh
vgs
```
![image](https://github.com/fourtimes/linux/assets/91359308/672b1dd1-54ea-4916-b8bf-26e1d47615d5)

9. Create a logical volume.
```sh
lvcreate -n app -L 5G /dev/myvg               # app - your partition name, 5G - allocate 5G storage, myvg - volume group
```
10. 
