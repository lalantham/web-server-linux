![Repo Image](https://github.com/lalantham/web-server-linux/blob/master/img.png)
# Web Server In Linux (Ubuntu)

>Complete Guild for install apache, php, mysql in linux and configure 

## 01 - Apache

	1.1 	Install Apache Server
				sudo apt install apache2

	1.2 - Servies
			Start, Stop, Restart Services
				sudo service apache2 start / stop / restart
			Status of Sevices
				sudo service apache2 status

	1.3 - Create Apache Server Root
			Create project folder
			Change project folder permision
				sudo chown -R group:user /path to dir
			Make /var/www readabale globaly
				sudo chmod -R 755 /var/html
	1.4 - Edit host file
			Edit host file in /etc/hosts
			add whatever.name to host file under localhost ip

	1.4 - Create Virtual Server
			Make a copy of /etc/apache2/sites-available/000-defaults.conf to whatever.name.conf
			Edit copyied .conf file to what ever we want
				ServerName = whatever.name
				ServerAdmin = Admin email
				DocumentRoot = link to project folder

	1.5 - Enable Virtual Server
			sudo a2ensite conf file name 'whatever.name.conf'


	1.6 - Restart Apache2
			sudo service apache2 restart , sudo systemctl reload apache2


## 02 - PHP

	2.1 - Install PHP
			sudo apt install php libapache2-mod-php

## 03 - PHP Mysql Module

	2.1 - Install PHP
			php -v
			dpkg --list | grep 'php.*mysql'

## 04 - Mysql

	3.1 - Install mysql

		- Method 01
			sudo apt install mysql-server
			Enter root password to promt
			sudo apt install phpmyadmin
			edit apache conf file and add "include /etc/phpmyadmin/apache.conf
			username = root / password = password which entered to prompt
			Restart apache
			============================================================
			sudo mysql_secure_installation
			sudo mysql
			SELECT user,authentication_string,plugin,host FROM mysql.user;
			ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
			FLUSH PRIVILEGES;
			SELECT user,authentication_string,plugin,host FROM mysql.user;
			
		- Method 02
			sudo apt install mysql-server
			Enter root password to promt
			install sql client and use credentials to login [Ex - DBeaver]
			username = root / password = password which entered to prompt
## 05 - Extras

	4.1 - Reset My Sql Password
			sudo /etc/init.d/mysql stop	
			sudo mkdir /var/run/mysqld
			sudo chown mysql /var/run/mysqld
			sudo mysqld_safe --skip-grant-tables&
			sudo mysql --user=root mysql
			UPDATE mysql.user SET authentication_string=null WHERE User='root';
			flush privileges;
			ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_password_here';
			flush privileges;
## 06 - Extras

	4.1 - Virual Host Custom Script
			https://github.com/lalantham/virtualhost
