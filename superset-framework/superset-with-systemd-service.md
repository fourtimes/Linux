## Superset Installation using systemd service for ubuntu

```cmd
sudo apt install build-essential libssl-dev libffi-dev python3-dev python3-pip libsasl2-dev libldap2-dev default-libmysqlclient-dev -y
```
Python Virtual Environment
```py
pip install virtualenv
```
You can create and activate a virtual environment using:
```py
sudo apt install python3.10-venv -y

python3 -m venv /home/ubuntu/venv

. /home/ubuntu/venv/bin/activate

```
Installing and Initializing Superset
```py
pip install apache-superset
```
Create a SECRET-KEY
```cmd
openssl rand -base64 42 # add this secret key to systemd service configuration file
```
Then, you need to initialize the database:
```py
superset db upgrade
```
Finish installing by running through the following commands:
```py
# Create an admin user in your metadata database (use `admin` as username to be able to load the examples)
superset fab create-admin

# Load some data to play with
superset load_examples

# Create default roles and permissions
superset init
```
Create the systemd service
```service
[Unit]
Description=Apache Superset
After=network.target

[Service]
User=ubuntu
Group=ubuntu
WorkingDirectory=/home/ubuntu/venv
ExecStart=/home/ubuntu/venv/bin/superset run -p 8088 --with-threads --reload --debugger --host 0.0.0.0
Environment="PATH=/home/ubuntu/venv/bin:$PATH"
Environment="SUPERSET_SECRET_KEY=your-secret-key"  # Replace with your actual SECRET_KEY
Environment="FLASK_APP=superset"
Restart=always
StandardOutput=journal
StandardError=journal

[Install]
WantedBy=multi-user.target
```
Once done the configuration, we need to follow the below steps.
```
sudo systemctl daemon-reload
sudo systemctl enable superset
sudo systemctl start superset
sudo systemctl status superset

# restart the service
sudo systemctl restart superset
```
Check the URL in browser - 
`http:\\pulic-ip:8088`

## KeyClock SSO with Superset
Install package for oauth
```
pip install Flask-OAuthlib Authlib
```
Create `superset_config.py` 
```py
#!/usr/bin/env python
# superset_config,py
 
from flask_appbuilder.security.manager import AUTH_OAUTH

AUTH_TYPE = AUTH_OAUTH
AUTH_USER_REGISTRATION = True
OAUTH_PROVIDERS = [
  {
    'name': 'keycloak',
    'token_key': 'access_token',
    'icon': 'fa-key',
    'remote_app': {
      'client_id': 'superset-ui-openid',
      'client_secret': 'your-client-secret',
      'api_base_url': 'https://{keycloackUrl}/realms/{your-realm}/protocol/',
      'jwks_uri':'https://{keycloackUrl}/realms/{your-realm}/protocol/openid-connect/certs',
      'server_metadata_url': 'https://{keycloackUrl}/realms/{your-realm}/.well-known/openid-configuration',
      'client_kwargs': {
          'scope': 'openid email',
          'roles_key': 'realm_access.roles'
      },
      'access_token_url': 'https://{keycloackUrl}/realms/{your-realm}/protocol/openid-connect/token',
      'authorize_url': 'https://{keycloackUrl}/realms/{your-realm}/protocol/openid-connect/auth',
      'userinfo_uri': 'https://{keycloackUrl}/realms/{your-realm}/protocol/openid-connect/userinfo',
      'logout_url': 'https://{keycloackUrl}/realms/{your-realm}/protocol/openid-connect/logout?redirect_uri=http://54.165.160.141:8088/logout'
      }
  }
]

# map keycloak role to superset role
AUTH_ROLES_MAPPING = {
    'prd-superset-admin': ['Admin', 'sql_lab'],
    'prd-superset-public': ['Public'],
    'prd-superset-alpha': ['Alpha'],
    'prd-superset-reader': ['Gamma'],
}
```


Add the `superset_config.py` file in systemd service file
```service
[Unit]
Description=Apache Superset
After=network.target

[Service]
User=ubuntu
Group=ubuntu
WorkingDirectory=/home/ubuntu/venv
ExecStart=/home/ubuntu/venv/bin/superset run -p 8088 --with-threads --reload --debugger --host 0.0.0.0
Environment="PATH=/home/ubuntu/venv/bin:$PATH"
Environment="SUPERSET_SECRET_KEY=your-secret-key"  # Replace with your actual SECRET_KEY line 23
Environment="FLASK_APP=superset"
Environment="SUPERSET_CONFIG_PATH=/home/ubuntu/superset_config.py"  # If you have a custom configuration
Restart=always
StandardOutput=journal
StandardError=journal

[Install]
WantedBy=multi-user.target
```
Again start the systemd service
```cmd
sudo systemctl daemon-reload

sudo systemctl start superset

sudo systemctl status superset

```
once done, check with browser using the below url:
```url
# if we use local server
http://localhost:8088

# if we use ec2 server
http://(public-ip):8088
```
## Reverse Proxy with Superset
Install the nginx
```
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl status nginx
```
Configure custom vhost file

```sh
# sudo vim /etc/nginx/conf.d/your-domain

server {
    listen 80;
    server_name your-domain;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    server_name your-domain;


    ssl_certificate /etc/nginx/ssl/certificate.crt;
    ssl_certificate_key /etc/nginx/ssl/private.key;

    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers 'HIGH:!aNULL:!MD5';
    ssl_prefer_server_ciphers on;

    location / {
        proxy_pass http://(publicIP):8088; # Replace with your application's address and port
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_buffering off;

        access_log /var/log/nginx/your-domain.access.log;
        error_log /var/log/nginx/your-domain.error.log;
    }
}
```
copy the file sites-enabled from conf.d
```cmd
ln -s /etc/nginx/conf.d/your-domain ./
```
Restart the service
```cmd
sudo systemctl restart nginx
```
Validate the nginx vhost file
```
sudo nginx -t
```
Check with browser - http://your-domain
