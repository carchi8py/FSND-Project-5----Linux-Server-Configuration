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
