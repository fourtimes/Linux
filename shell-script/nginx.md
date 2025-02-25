### Install the nginx server 
```sh
#!/bin/bash
sudo apt update
sudo apt install nginx -y
sudo systemctl enable nginx
sudo echo '<h1 style="color:blue;">This is Private 1 instance</h1>' > /var/www/html/index.html
sudo systemctl start nginx
sudo systemctl status nginx
```
