# Steghub LAMP Stack on AWS EC2
LAMP stack project on AWS EC2 with virtual host and PHP

## Challenge
This project involved setting up a **LAMP stack (Linux, Apache, MySQL, PHP)** on an **AWS EC2 instance** and creating a **virtual host** to host a simple website.

Challenges I faced included:

- **SSH access issues:** Needed to correctly set the `.pem` key path to connect.  
- **File permission problems:** Had to adjust ownership and permissions for Apache to serve files.  
- **Virtual host configuration:** Understanding how to create, enable, and reload the virtual host.  
- **Editing files in terminal:** Learning to edit, save, and exit files in `nano`/`vi`.

## Implementation
Step-by-step actions I performed:

**Set up EC2 instance** and configured SSH access with `.pem` key.  

**Installed LAMP stack:**

```bash
sudo apt update
sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql
sudo systemctl status apache2
sudo systemctl status mysql
php -v

Created project directory and virtual host:
sudo mkdir /var/www/projectlamp
sudo chown -R $USER:$USER /var/www/projectlamp
sudo nano /etc/apache2/sites-available/projectlamp.conf
sudo a2ensite projectlamp.conf
sudo a2dissite 000-default.conf
sudo systemctl reload apache2

Created test files

index.html for testing the virtual host.

info.php to display PHP info:

php
<?php
phpinfo();
?>

Adjusted permissions:
sudo chown -R www-data:www-data /var/www/projectlamp
sudo chmod -R 755 /var/www/projectlamp

Accessed website in browser:

URL: http://54.91.184.36/projectlamp/info.php
Confirmed PHP is running and the virtual host works.

Success

LAMP stack is fully installed and operational.

Apache serves files from /var/www/projectlamp.

PHP files execute correctly.

Successfully navigated SSH, permissions, and file editing as a beginner.

Access: http://54.91.184.36/projectlamp/info.php


Screenshots
<img width="1920" height="1080" alt="InfoPHP" src="https://github.com/user-attachments/assets/c65c0e38-a5c0-4772-9dea-b2f55618780a" />
<img width="1920" height="1080" alt="Home LAMP" src="https://github.com/user-attachments/assets/75c81cf7-e30f-42db-9792-f8f79f2d77e6" />
<img width="1920" height="1080" alt="EC2 SYSTEM INFO" src="https://github.com/user-attachments/assets/20fada45-6caa-4b90-bd2f-ba2ca9e2b7a9" />
![EC2 INSTANCE](https://github.com/user-attachments/assets/350c8b39-0786-4d31-a44a-56eb056d39b1)
<img width="1920" height="1080" alt="Apache2 Page" src="https://github.com/user-attachments/assets/d6493ad2-c3b7-49b9-a456-77887801a6ae" />
<img width="1920" height="1080" alt="INSTANCE LAUNCH" src="https://github.com/user-attachments/assets/f49e86c3-c682-4616-a1bd-17bf4799b461" />
