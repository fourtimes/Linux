### Install the apache2 server
```sh
#!/bin/bash
sudo apt update
sudo apt install apache2 -y
sudo systemctl enable apache2
sudo chmod 777 /var/www/html -R
sudo echo '<h1 style="color:blue;">This is apache2 instance</h1>' > /var/www/html/index.html
sudo systemctl start apache2
sudo systemctl status apache2
```
### Uninstall the apache2 server
```sh
#!/bin/bash
sudo service apache2 stop
sudo apt-get purge apache2 apache2-utils apache2-bin apache2.2-common -y
sudo apt-get autoremove -y
# whereis apache2 => find the apache file
sudo rm -rf /etc/apache2
```
[or]
```sh
#!/bin/bash
sudo service apache2 stop
sudo apt-get remove apache2
sudo apt-get purge apache2
sudo apt-get autoremove
whereis apache2
sudo rm -rf /etc/apache2
which apache2
sudo rm -rf /usr/sbin/apache2
which apache2 # should be get a blank details
```
