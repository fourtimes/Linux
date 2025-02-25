
How to Completely Remove PHP from Ubuntu

```sh
sudo apt-get purge 'php*' 
sudo rm -rf /etc/php/
sudo apt-get autoremove
php -v
```
