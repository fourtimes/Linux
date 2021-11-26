```bash
# create group user
sudo groupadd username

# one group into one user
sudo usermod -a -G groupname username 

# muliple group in one user
usermod -a -G group1,group2,group3 username

# remove a user from group
sudo gpasswd -d  username groupname

# user information
sudo usermod -c "This is demo user" username

# Add the users into docker group
sudo usermod -aG docker ubuntu
 ```
