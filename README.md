## INTRODUCTION
The LAMP ( Linux, Apache, MySQL, PHP ) stack is a popular open-source web development platform used to build dynamic websites and web applications. Using LAMP, developers can deploy fully functional web applications quickly, leveraging widely supported technologies.

## LAMP Stack Web Application Deployment on AWS

**Project Overview**

This project demonstrates the deployment of a web application using the LAMP stack on AWS EC2. The LAMP stack includes:

Linux – Operating system for server environment.

Apache – Web server to serve HTTP requests.

MySQL – Relational database management system for data storage.

PHP – Server-side scripting language to create dynamic web content.

The main goal was to set up a fully functional web application environment in the cloud, integrating database operations with front-end interaction.

## AWS Infrastructure Setup
 **AWS EC2 Instance**
Instance Type: t2.micro (free tier)
OS: Ubuntu 20.04 LTS
Security Group: Allowed HTTP (port 80) and SSH (port 22) traffic
Key Pair: Used for SSH access to the instance
<img width="1920" height="1080" alt="00-EC2-Instance Launch" src="https://github.com/user-attachments/assets/ca8532e4-2554-4a1e-91a6-5cfe747a7e84" />
<img width="1920" height="1080" alt="01-EC2 Instance-Running" src="https://github.com/user-attachments/assets/cc0d7ac2-845c-49be-a288-9a7fb579f07f" />

## SSH Configuration
**Connected to the instance using a private key (.pem) file**

```
ssh -i "YourKey.pem"
ubuntu@<EC2-public-IP>
```
```
sudo apt update && sudo apt upgrade -y
```
<img width="1920" height="1080" alt="03-Connect to Instance" src="https://github.com/user-attachments/assets/ec70921d-735a-4450-9005-3fabe876c1f3" />
<img width="1920" height="1080" alt="SSH config" src="https://github.com/user-attachments/assets/626431a3-bf3b-4477-8103-49e57a451f4f" />


## LAMP Stack Installation
**Apache Web Server**
Install Apache
```
sudo apt update
```
```
sudo apt install apache2
```
```
sudo systemctl status apache2
```
**Apache browser test**
<img width="1920" height="1080" alt="05-Apache2 Page" src="https://github.com/user-attachments/assets/0940a9e5-2530-48bd-baed-a961156b63d9" />

## MySQL Database
**Installed MySQL and secured it**

```
sudo apt install mysql-server
```
```
sudo mysql
```
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
exit
```
```
sudo mysql_secure_installation
```
```
CREATE DATABASE myapp;
CREATE USER 'appuser'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON myapp.* TO 'appuser'@'localhost';
```
```
sudo mysql -p
exit
```
## PHP Installation
```
sudo apt install php libapache2-mod-php php-mysql
sudo systemctl restart apache2
```
3. Apache & PHP Verification
```
sudo systemctl status apache2
```
Verified PHP installation
```
php -v
```
<img width="1920" height="1080" alt="Home LAMP" src="https://github.com/user-attachments/assets/4883be4a-bba0-46c6-bcec-bc36d9cd395d" />

## Directory Setup

**Created the project directory and added web files**
```
sudo mkdir -p /var/www/projectlamp/
```
**Assign ownership**

```
sudo chown -R $USER:$USER /var/www/projectlamp
sudo chmod -R 755 /var/www/projectlamp
```
**index.html: Contains a simple HTML message**

info.php: Displays PHP info
```
<?php
phpinfo();
?>
```
## Virtual Host Configuration

Created and enabled a virtual host configuration file:
```
sudo nano /etc/apache2/sites-available/projectlamp.conf
```
```
<VirtualHost *:80>
    ServerAdmin projectlamp
    DocumentRoot /var/www/projectlamp/
    ServerName projectlamp.local
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

**Enabled the site and reloaded Apache**
```
sudo a2ensite projectlamp.conf
```
```
sudo systemctl reload apache2
```
<img width="1920" height="1080" alt="InfoPHP" src="https://github.com/user-attachments/assets/1d9f68cc-e29e-427f-93c3-317bb26d36c9" />

## Verification

Tested the setup in a web browser:

http://54.91.184.36/projectlamp/info.php

Result: PHP info page displayed, confirming PHP is working correctly.

## Summary

Instance: AWS EC2 t2.micro, Ubuntu 22.04 LTS
Environment: Apache2, MySQL, PHP
Project directory: /var/www/projectlamp/
Virtual host: projectlamp.conf
PHP verified via: info.php
Publicly accessible at: http://54.91.184.36/projectlamp/info.php

✅ Project successfully implemented. All required steps completed, and PHP is functional on the server.


**Self-Study Documents**

The following documents were referenced to build knowledge on LAMP stack and Linux commands:

LAMP Basics
 – Overview of Linux, Apache, MySQL, PHP and their roles in web development.

Linux Commands Reference
 – Cheat sheet of essential Linux commands used in this project.

** References / Resources**
Personal self-study materials
LAMP Stack tutorials and documentation
