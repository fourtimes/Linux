## Superset Installation for ubuntu

```cmd
sudo apt-get install build-essential libssl-dev libffi-dev python3-dev python3-pip libsasl2-dev libldap2-dev default-libmysqlclient-dev
```
Python Virtual Environment
```py
pip install virtualenv
```
You can create and activate a virtual environment using:
```py
sudo apt install python3.10-venv -y
python3 -m venv venv
. venv/bin/activate
```
Installing and Initializing Superset
```py
pip install apache-superset
```
Create a SECRET-KEY
```cmd
openssl rand -base64 42
```
Then, define mandatory configurations, SECRET_KEY and FLASK_APP:
```env
# sudo vim /home/ubuntu/.bashrc

export SUPERSET_SECRET_KEY=YOUR-SECRET-KEY   # enter the above openssl SECRET_KEY
export FLASK_APP=superset
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

# To start a development web server on port 8088, use -p to bind to another port
superset run -p 8088 --with-threads --reload --debugger   # allow single host
                        [or]
superset run -p 8088 --with-threads --reload --debugger --host 0.0.0.0   # allow all hosts
```
Check the browser using the below details
```
# if we use local server
http://localhost:8088

# if we use remote server
http://public-ip:8088
```
<img width="1426" alt="image" src="https://github.com/user-attachments/assets/f0ed109c-632a-426f-aa2e-9424c0986a42" />


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
Environment="SUPERSET_SECRET_KEY=Vm/qJyTZf3O9Ix6i3U1HClazf86teLDtza6aY1IVfUzA8Y054PvoIiZX"
Environment="FLASK_APP=superset"
Restart=always
StandardOutput=journal
StandardError=journal

[Install]
WantedBy=multi-user.target
```
