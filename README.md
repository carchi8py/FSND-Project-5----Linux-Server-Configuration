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
