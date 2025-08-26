**LAMP Stack Project Report**

**Project Overview**
This project involved setting up a LAMP (Linux, Apache, MySQL, PHP) stack on an Ubuntu server and deploying a simple web application. The goal was to create a project directory, configure a virtual host, and verify PHP functionality.

**Environment Setup**
1. AWS EC2 Instance:
Instance Type: t2.micro (free tier)
OS: Ubuntu 20.04 LTS
Security Group: Allowed HTTP (port 80) and SSH (port 22) traffic
Key Pair: Used for SSH access to the instance

2. LAMP Stack Installation:
sudo apt update
sudo apt install apache2
sudo apt install mysql-server
sudo apt install php libapache2-mod-php php-mysql

3. Apache & PHP Verification
sudo systemctl status apache2
Verified PHP installation
php -v

**Steps Performed**
1. Directory Setup
Created the project directory and added web files
sudo mkdir -p /var/www/projectlamp/
sudo nano /var/www/projectlamp/index.html
sudo nano /var/www/projectlamp/info.php

index.html: Contains a simple HTML message
info.php: Displays PHP info

<?php
phpinfo();
?>

2. Virtual Host Configuration
Created and enabled a virtual host configuration file:
sudo nano /etc/apache2/sites-available/projectlamp.conf

<VirtualHost *:80>
    ServerAdmin admin@example.com
    DocumentRoot /var/www/projectlamp/
    ServerName projectlamp.local
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

**Enabled the site and reloaded Apache**
sudo a2ensite projectlamp.conf
sudo systemctl reload apache2

3. Verification
Tested the setup in a web browser:
http://54.91.184.36/projectlamp/info.php
Result: PHP info page displayed, confirming PHP is working correctly.

4. Summary

Instance: AWS EC2 t2.micro, Ubuntu 20.04 LTS
Environment: Apache2, MySQL, PHP
Project directory: /var/www/projectlamp/
Virtual host: projectlamp.conf
PHP verified via: info.php
Publicly accessible at: http://54.91.184.36/projectlamp/info.php

✅ Project successfully implemented. All required steps completed, and PHP is functional on the server.

Screenshots
<img width="1920" height="1080" alt="InfoPHP" src="https://github.com/user-attachments/assets/c65c0e38-a5c0-4772-9dea-b2f55618780a" />
<img width="1920" height="1080" alt="Home LAMP" src="https://github.com/user-attachments/assets/75c81cf7-e30f-42db-9792-f8f79f2d77e6" />
<img width="1920" height="1080" alt="EC2 SYSTEM INFO" src="https://github.com/user-attachments/assets/20fada45-6caa-4b90-bd2f-ba2ca9e2b7a9" />
<img width="1920" height="1080" alt="EC2 INSTANCE" src="https://github.com/user-attachments/assets/7f8239fd-704e-42b7-a7e9-abbe908884a3" />
<img width="1920" height="1080" alt="Apache2 Page" src="https://github.com/user-attachments/assets/d6493ad2-c3b7-49b9-a456-77887801a6ae" />
<img width="1920" height="1080" alt="INSTANCE LAUNCH" src="https://github.com/user-attachments/assets/f49e86c3-c682-4616-a1bd-17bf4799b461" />
