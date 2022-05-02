# ssh connection:
1. To acces the key file  authentication
2. To access the password authentication


**1. ssh Key file authentication:-**

 To Access the read permission ssh:-
```bash
 chmod 0400 (key-file name)
```

 To connect server using ssh:-
```bash
 ssh -i (key-file-name) login_username@ip_address
```

 To update the system:- 
```bash
 sudo apt update
```
 Install the packages:- 
```bash
 sudo apt install (package-name)
```
**2. ssh password authentication:-**

1. To connect server using ssh:-
```bash
 ssh login_username@ip_address
```
2. To update the system:-
```bash
 sudo apt update
```
3. Install the packages:- 
```bash
 sudo apt install (package-name)
```
**Five components of Linux:**
1. Networking
2. User/group 
3. Package
4. Storage
5. Service
