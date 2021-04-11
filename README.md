## Here we are going to create a full running project using vagrant 
Aim: User can send a request to the interective application through Nginx server to tomcat server where the application is running. The tomcat server takes the request and\ send the mesaage to rabitMQ message broker. Then the data will cached into the memcached and then to mySql database.
##### Workflow:
- set-up the below servers\
* database (MySql) as db01
* memcached as mc01
* rabitMQ as rb01
* tomcat as app01
* nginx as ngi01

First, we will do the server setup by bringing up the respective VM
Second, we will do the installatin and configuarion on each respective server
Third, we will build the application from the source code and deploy intothe tomcat server
Finally, we will validate the applicatin from browser
