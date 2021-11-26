```bash

# create a ssh key
ssh-keygen

# Copying Your Public Key Using ssh-copy-id
ssh-copy-id username@remote_host

Refference:-
    localhost- ip address;
    remote_host - website;

# Authenticating to Your Server Using SSH Keys
ssh username@remote_host

# Disabling Password Authentication on your Server
sudo vim /etc/ssh/sshd_config
    filename: /etc/ssh/sshd_config
    PubkeyAuthentication `no`
    PasswordAuthentication `no`

# validation
sshd -t

# restart the ssh service
sudo systemctl restart ssh

```
