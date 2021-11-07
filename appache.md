```bash
# Finding Apache2 Document Root
grep -i 'DocumentRoot' /etc/apache2/sites-available/000-default.conf
grep -i 'DocumentRoot' /etc/apache2/sites-available/default-ssl.conf

# To change Apache's root directory, run:
 cd /etc/apache2/sites-available

# To find what are the directories in Appache2
ls -la
 
# To create a another file in Appache2 
sudo nano 000-default.conf (`DocumentRoot /path/your-project-name`)

# restart the Appache2 Service
sudo service apache2 restart
```