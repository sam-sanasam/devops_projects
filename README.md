## Here we are going to create a full running project using vagrant 
Aim: User can send a request to the interective application through Nginx server to tomcat server where the application is running. The tomcat server takes the request and\ send the mesaage to rabitMQ message broker. Then the data will cached into the memcached and then to mySql database.
##### Workflow:
set-up the below servers
* database (MySql) as db01
* memcached as mc01
* rabitMQ as rb01
* tomcat as app01
* nginx as ngi01

First, we will do the server setup by bringing up the respective VM\
Second, we will do the installatin and configuarion on each respective server\
Third, we will build the application from the source code and deploy intothe tomcat server\
Finally, we will validate the applicatin from browser


#### Lets start database server configuration
Update the system
$ yum update -y

Set up a variable which can use for passward whcih accessing the DB
$ DATABASE_PASS = "admin123"
However this variable is not static, means it will lose when we run next time. SO we need to make it static by inserting\
it in the '/etc/profile' file
$ vi /etc/profile
It is open up the profile file and insert the DATABASE_PASS = "admin123"  variable just at the bottom . save the file .
So to make the variable in the profile file permanent , we have to run the below command.
$ source /etc/profile

Now, we will install the packages:\
* git
* mariadb-server

$ yum install git mariadb-server -y
After installation completion, run the below 2 command to start the service
$ systemctl start mariadb
$ systemctl enable mariadb
$ systemctl status mariadb

After the status "running" confirmation, run the below command as a part of mariadb installation.For ref.  https://mariadb.com/kb/en/mysql_secure_installation/
$ mysql_secure_installation
Enter current password for root (enter for none): <hit enter>
Set root password? [Y/n] <Y>
  new passward: <enter the password which has set in the DATABASE_PASS variable>
  reenter the passward:
Remove anonymous users? [Y/n] <Y>
Disallow root login remotely? [Y/n] n
Remove test database and access to it? [Y/n] y
Reload privilege tables now? [Y/n] y
  
  
  NOw , All done!!
  
  Let's try by loggin inside the database
  $mysql -u root -p
  
*Welcome to the MariaDB monitor.  Commands end with ; or \g.*
*Your MariaDB connection id is 9*
*Server version: 5.5.68-MariaDB MariaDB Server*

*Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.*

*Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.*

*MariaDB [(none)]>*

The above output shows that we are inside the database.

#### Le

