Five components of Linux:; 1) Networking 2) User/group 3) Package 4) Storage 5) Service.

To access the key file authentication:-

1. To Access the read permission ssh:-**chmod 0400 (key-file name)**

2. To connect server using ssh:-**ssh -i (key-file-name) login_username@ip_address**

3. To update the system:- **sudo apt update**

4. Install the packages:- **sudo apt install (package-name)**

To access the password authentication:-

1. To connect server using ssh:-**ssh login_username@ip_address**

2. To update the system:- **sudo apt update**

3. Install the packages:- **sudo apt install (package-name)**

for i in {1..10}; do
echo \$i
done

GoalKicker.com – Bash Notes for Professionals 40
case "$BASH_VERSION" in
 [34]*)
    echo {1..4}
    ;;  
  *)
    seq -s" " 1 4
esac