# FSND-Project-5----Linux-Server-Configuration

##Description:
In this project we set up and secured a publicy accessible server.

## IP Address
* IP address: http://52.36.49.232/
* Ssh Port: 2200
* Username: grader
* URL: http://ec2-52-36-49-232.us-west-2.compute.amazonaws.com/

## Steps to set up server

### User Creation 
* Create a new Users
```
  $sudo adduser grader
```
* Give the new user sudo permissions by adding the following line `grader ALL=(ALL) NOPASSWD:ALL` in to grader file
```
  $sudo vi /etc/sudoers.d/grader
```

### Change SSH port from 22 to 2200. To do this we edit the port line in the file below from 22 to 2200. And then restart the ssh service
```
  sudo vi /etc/ssh/sshd_config 
  sudo service sshd restart
```

### Update Packages
* First check for packages to update
```
  $sudo apt-get update
```
* Then Upgrade the packages them selfs. 
```
  $sudo apt-get upgrade
```

### Seting up a firewall
* First block all incomming ports. This way we only grant access to the one we need.
```
  $sudo ufw default deny incoming
```
* Next we set the ports we want open. Since we changed the SSH port we can't use the simple allow ssh as that will open port 22. So we will have to specify the specific port instead
```
  sudo ufw allow 2200
  sudo ufw allow www
  sudo ufw allow 123
  sudo ufw enable
```
### Set the Timezone to UTC
```
  sudo cp /usr/share/zoneinfo/UTC /etc/localtime
```

### Install software
* first install apache2. 
```
  sudo apt-get install apache2
```
* Next mod WSGI
```
  sudo apt-get install libapache2-mod-wsgi
```
* Next the database. 
```
sudo apt-get install postgresql
```
* Git 
```
sudo apt-get install git-all
```
* Python's psycopg2
```
sudo apt-get install python-psycopg2
```

### Install the Python Modules we'll need to get this running
*To make life easier we are going to get pip so we can install what we need with one line
```
  wget https://bootstrap.pypa.io/get-pip.py
```
*Then install pip
```
python get-pip.py
```
*Install the python modules i need to get the flask application to run
```
  pip install Flask
  pip install SQLAlchemy
  pip install --upgrade oauth2client
```
