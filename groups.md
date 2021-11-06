```bash
# create group user
sudo groupadd ashli

# one group into one user
sudo usermod -a -G ashli demo 

# muliple group in one user
usermod -a -G group1,group2,group3 exampleusername

# remove a user from group
sudo gpasswd -d  demos ashli

# user information
sudo usermod -c "This is demo user" demo

# Add the users into docker group
sudo usermod -aG docker ubuntu
 ```