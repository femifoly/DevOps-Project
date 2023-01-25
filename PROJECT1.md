# <ins>WEB STACK IMPLEMENTATION IN AWS</ins> 
## Linux, Apache, MySQL, PHP - LAMP STACK
Welcome to my first project! In this project, I will be exploring the use of technology stack to create different solutions possible to deploy our applications, websites etc. A technology stack is a set of frameworks and tools used to develop a software product. They are specifically chosen to work together in creating a well-functioning software.
The fuctionality of the Stack is hereby listed as:

| STACK | FUNCTION |
| - | - |
| Linux | Operating Sysytem |
| Apache| Web Server |
| MySQL | Database |
| PHP | Programing Language |

---
Before I get into the fundamentals, I created an AWS account and also created a IAM User for the account. It is best practice to access the AWS account as a user rather than accessing it as a root user. 


![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/iamuser1.jpg)


![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/iamuser.jpg)

AWS service for hosting a virtual machine is the Elastic Compute Cloud (ECS). I am going to create an EC2 instance to host our VM which will run Ubuntu (Linux 
Distribution).

Before proceeding with the creation of an EC2 instance, select the desired and closest region to you. The following are the factors to consider before deciding the AWS region to choose:

* Latency and proximity

* Security and regulatory compliance

* Service Level Agreements (SLA)

And finally, the most important is the **Cost**

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/region.jpg)
---

**Click on Services, Compute then select EC2.**

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/EC2.jpg)
---

**Scroll down, click Lauch Instances and name your new instance.**

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/EC21.jpg)
---

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/EC22.jpg)
---

**Ubuntu Server 22.04, t2.micro family type is selected to run on the instance.**

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/EC23.jpg)
---

**Next, a key pair is created to enable secure connection to the instance. The private key (.pem) should be saved securely to prevent unauthorized access to the server.**

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/EC24.jpg)
---

Next, I configured the network setting by creating a new security group that will act as firewall to control traffic in and out of our instance. For me to be be able to access the instance from my windows computer and from the internet, I need to enable SSHport 22 and HTTP port 80. To do this, I created inbound rules for the ports. Because my computer runs on Windows, I will need to download and install an ssh client to establish connectivity with the instance. For this project, I will install Mobarxterm.
**Note** - EC2 has created a default Virtual Private Cloud (VPC) where the instance server is situated which means both public and private IPs have been authomatically generated for the instance. I will leave the root storage setting as default for the purpose of this project. We can go ahead and launch the new instance!

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/sg.jpg)
---
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/sg1.jpg)
---

Our server is up and running
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/instance.jpg)
---

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/instance1.jpg)

## Connecting to EC2 terminal

After installing Mobaxterm, I confirgured the tool to connect to our guest operating system (Ubuntu) running on AWS virtual server.

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/mob.jpg)
---

To do this:
* Open a new session by clicking session in the top left corner
* Click on SSH with key icon
* Copy the public IP address from the instance into the remote host
* Click on advance SSH settings
* Enable use private key

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/moba.jpg)
---

* Then click on the tab to upload the .PEM key we saved earlier when creating the key pair.
* Click ok and click accept on the pop-up window.

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/mob1.jpg)
---

Login detail is required to authorise access to our remote server. To acquire this, click connect on the instance page and you will the username required by the SSH Client. Ubuntu is our username in this case.

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/hostusername.jpg)
---

As you can see, the SSH client has acquired the instance private IP and yes we have access to our remote server!

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/mob2.jpg)
=======

### Having launched our instance on AWS to run Linux distribution - Ubuntu - I will commence the project to deploy a web solution based on LAMP stack by implementing the steps bellow:


## Step 1 - Installing Apache and Updating the Firewall

* Apache is installed using the Ubuntu package manager ~ *apt*
```
sudo apt update
sudo apt install apache2
```
* To verify that Apache2 is installed and running as a service on our OS, use the following commmand:
```
sudo systemctl status apache2
```
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/apache1.jpg?raw=true)
Now that we have installed our web server, we need to open port 80 and port 443 to allow access to the server through the internet.
To do this, we need to to go back to our EC2 instance and add new inboubd rules to enable the ports.
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/tcp%20.jpg?raw=true)

* To verify and check that we can access it locally in our ubuntu shell and from the internet, run:
```
curl http://localhost:80
```

* To confirm that our web server is up and running, copy and paste your public IP in a browser as follows: 
```
http//<your public IP>:80
```
* If you see the following page, then your web server is now correctly installed and accessible through your firewall:
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/apache2.jpg)

## STEP 2 - Installing MySQL
We need to install the database system to be able to store and manage data for our website. MySQL creates a database for storing and manipulating data, defining the relationship of each table, it is a popular database management system used within PHP environments.

To install mysql-server, run:
```
sudo apt -y install mysql-server
```
After the installation it is recommended that we run a security script that comes pre-installed with MySQL. This script will remove some insecure default settings and lockdown access to our database system.

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/mysql.jpg)

Start the interactive Script by running:
This will allow you to configure the VALIDATE PASSWORD PLUGIN.
```
sudo mysql_secure_installation
```
* To verify access to the MySQL Console, run the following command:
```
sudo mysql
```
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/mysql1.jpg)

*To exit the MySQL Console, type: exit
```
mysql> exit
```
## STEP 3 - Installing PHP

We have installed Apache to serve our content and MySQL installed to store and manage our data. PHP is the component of our setup that will process code to display dynamic content to the final user. In addition to the php package, we’ll need php-mysql, a PHP module that allows PHP to communicate with MySQL-based databases. We’ll also need libapache2-mod-php to enable Apache to handle PHP files. Core PHP packages will automatically be installed as dependencies.

* Run the following command to install all 3 packages:
```
sudo apt -y install php libapache2-mod-php php-mysql
```
* Once the installation is finished, you can run the following command to confirm your PHP version:
```
php -v
```
![]{https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/php.jpg}

At this point, LAMP stack is completely installed and fully operational.
To test our setup with a PHP Script, it's best to setup a proper Apache Virtual Host to host our website's file and folders. Virtual Host allows multiple websites to be located on a single machine and users of the websites will not even notice it. This will take us to the next step.

## STEP 4 - Creating a Virtual Host for your Website using Apache

* A domain called projectlamp is set up for this project.

Apache on Ubuntu 22.04 has one server block enabled by default that is configured to serve documents from the /var/www/html directory. We will leave this configuration as is and will add our own directory next next to the default one.

* Create the directory for projectlamp using ‘mkdir’ command as follows:
```
sudo mkdir /var/www/projectlamp
```

* Next, assign ownership of the directory with the $USER environment variable, which will reference current user.
```
sudo chown -R $USER:$USER /var/www/projectlamp
```
* We can now open a new configuration file in Apache’s sites-available directory using our preferred command-line editor. Here, we’ll be using vi
```
sudo vi /etc/apache2/sites-available/projectlamp.conf
```
This will create a new blank file. Paste in the following bare-bones configuration by hitting on i on the keyboard to enter the insert mode, and paste the text:
```
<VirtualHost *:80>
    ServerName projectlamp
    ServerAlias www.projectlamp 
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/projectlamp
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/vh.jpg)
* To save and close the file, press ESC and type :wqa!
* Run the following command to view and confirm the new files in the sites available directory:
```
sudo ls /etc/apache2/sites-available
```
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/vh1.jpg)

With this VirtualHost configuration, we’re telling Apache to serve our website using /var/www/projectlamp as the web root directory. If we like to test Apache without a domain name, we can remove or comment out the options ServerName and ServerAlias by adding a # character in the beginning of each option’s lines. Adding the # character there will tell the program to skip processing the instructions on those lines.
* We can now use a2ensite command to enable the new virtual host:
```
sudo a2ensite projectlamp
```
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/vh2.jpg)
* We might need to disable the default website that comes installed with Apache. This is required if we are not using a custom domain name, because in this case Apache’s default configuration would overwrite our virtual host. To disable Apache’sdefault website use a2dissite command, type:
```
sudo a2dissite 000-default
```
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/vh3.jpg)
* To make sure your configuration file doesn't contain syntax errors, run:

```
sudo apache2ctl configtest
```
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/vh4.jpg)
* Finally, reload Apache so these changes take effect:

```
sudo systemctl reload apache2
```
The new website is now active, but the web root /var/www/projectlamp is still empty. Create an index.html file in that location so that we can test that the virtual host works as expected:

* Type and run :
* 
```
sudo vi /var/www/projectlamp/index.html
```
or
```
sudo echo 'Hello LAMP, I am Kolawole Oduremi' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' 
(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html
```
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/html.jpg)
From the browser, I can open the website URL using IP address:

```
http://<public-ip-address>:80
```
or can also browse using the public dns.

```
http://<Public-DNS-Name>:80
```
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/html1.jpg)
You can leave this file in place as a temporary landing page for your application until you set up an index.php file to replace it. Once you do that, remember to remove or rename the index.html file from your document root, as it would take precedence over an index.php file by default.

To check your Public IP from the Ubuntu shell, run :
```
(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 
(curl -s http://169.254.169.254/latest/meta-data/public-ipv4)
```
## STEP 5 - Enable PHP on the website

With the default DirectoryIndex settings on Apache, a file named index.html will always take precedence over an index.php file. This is useful for setting up maintenance pages in PHP applications, by creating a temporary index.html file containing an informative message to visitors. Because this page will take precedence over the index.php page, it will then become the landing page for the application. Once maintenance is over, the index.html is renamed or removed from the document root, bringing back the regular application page.

In case you want to change this behavior, you’ll need to edit the /etc/apache2/mods-enabled/dir.conf file and change the order in which the index.php file is listed within the DirectoryIndex directive:
```
sudo vim /etc/apache2/mods-enabled/dir.conf
```
#Change this: #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm #To this: DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
After saving and closing the file, you will need to reload Apache so the changes take effect:
```
sudo systemctl reload apache2
```
Finally, we will create a PHP Script to test the PHP is correctly installed and configured on our Server.
Now that we have a custom location to host our website's files and folders, we'll create a PHP test script to confirm that Apache is able to handle and process requests for PHP files.
Create a new file named index.php inside our custom web root folder:
```
vim /var/www/projectlamp/index.php
```
This will open a blank file. Add the following text, which is valid PHP code, inside the file:
```
<?php
phpinfo();
```

When you are finished, save and close the file, refresh the page and you will see a page similar to this :
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/php1.jpg)

This page provides information about your server from the perspective of PHP. It is useful for debugging and to ensure that your settings are being applied correctly.

If you can see this page in your browser, then your PHP installation is working as expected.

After checking the relevant information about your PHP server through that page, it’s best to remove the file you created as it contains sensitive information about your PHP environment -and your Ubuntu server. You can use rm to do so:

```
$ sudo rm /var/www/projectlamp/index.php
```
Note that it is a good practice to stop or terminate your AWS EC2 instances after the completion of your project.
Thank You
