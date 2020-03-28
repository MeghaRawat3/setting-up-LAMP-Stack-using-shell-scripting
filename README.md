# setting-up-LAMP-Stack-using-shell-scripting
A shell script for installing LAMP on Debian OS

## About LAMP 
The shortened form stands for **L**inux, **A**pache, **M**ySQL, and **P**HP that is used to set up web servers. The words most often used to describe LAMP are **stable, simple,** and **powerful**. It is considered as a stack is on the ground that each level infers off it's base layer. In the Working framework, Linux, is the base layer. At that point Apache, the web server sits on the operating system, and then database stores all the data served by the web server, and PHP or any other P* scripting language is utilized to drive and show all the information, and consider client connection.

Manually installing lamp on all servers can be repetitive and time consuming. Therefore, we have written a script that **installs LAMP configures the necessary permissions** and then, **starts the web server**.

## What this script does:
1. Updates the packages.
2. Install Apache web server
3. Install PHP and requirements
4. Install MySQL
5. Setting Permissions
6. Enabling Modules

## STEP 1: Creating file for the script 

```
sudo gedit lamp.sh
```
In the above command **gedit** is used to create file. Filename should be of format **<filename.sh>** .

## STEP 2: Updating Apt Packages and upgrading latest patches

```
sudo apt-get update -y && sudo apt-get upgrade -y
```
By running the above command it will update and upgrade the apt-get packages to their current versions in your system. It might take some time for the execution of this code. 

**NOTE:** Use the below command if the code shows error while execution.  
```
ps aux | grep -i apt
```

## STEP 3: Installing Apache2 Web server

```
sudo apt-get install apache2 apache2-doc apache2-mpm-prefork apache2-utils libexpat1 ssl-cert -y
```
The above command is used for installing the Apache web server on the linux which is acting as the base layer in LAMP stack.

## STEP 4: Installing MySQL

```
sudo apt-get install mysql-server mysql-client -y
```
The above command is used for installing MYSQL. It is used for collecting and storing the data as RDBMS.

## STEP 5: Installing PHP & Requirements

```
sudo apt-get install libapache2-mod-php7.0 php7.0 php7.0-common php7.0-curl php7.0-dev php7.0-gd php-pear php7.0-mcrypt php7.0-mysql -y
```
The above command is used for installing PHP and requirements. PHP an object oriented scripting language is used to display the data in MySQL.  

## STEP 6: Setting Permissions

```
sudo chown -R www-data:www-data /var/www
```
In the above command 
* the chown command changes the ownership to user:group i.e. www-data:www-data in our case.
* **-R** is used to change the ownership recursively for all files and directories in /var/www.

## STEP 7: Enabling Modules

```
sudo a2enmod rewrite
sudo phpenmod mcrypt
```
In the above command a2enmod enables apache2 module and phpenmod enables php module.

## STEP 8: Restarting Apache

```
sudo service apache2 restart
```
The above command is used to restart the apache2 web service.





**You can find the complete code at my Github [MeghaRawat3](https://github.com/MeghaRawat3/setting-up-LAMP-Stack-using-shell-scripting)**





















