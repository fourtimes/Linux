**ubuntu**
```bash
#!/usr/bin/env bash

# mysql-installation.sh
sudo apt update
sudo apt install mysql-server -y
sudo systemctl start mysql.service
sudo systemctl enable mysql.service
sudo systemctl status mysql.service
```

execution

```bash
bash kubectl-installation.sh
```
