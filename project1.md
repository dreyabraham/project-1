## documentation of project 1

 Project 1 is all about LAMP implimentation.

 the first command was `sudo apt update` which was succesful
 installed apache with the code `sudo apt install apache2` which was succesful.
 
 ![screeshot](./images/capture.PNG)

We have now launched our web server, now we are going to use the code `curl http://localhost:80` to access it locally in our ubuntu shell this is succesful.
Testing apache now on browser local ip  3.223.195.252

![screenshot](./images/Ubuntu.PNG)

Next step is installing mysql using the code `sudo apt install mysql-server` succesful.
using the `sudo mysql_secure_installation` we are going to secure our database.
![screenshot](./images/mysql.PNG)
using the `sudo mysql_secure_installation` we are gonna secure our database.
log in to mysql to be sure its working with the code `sudo mysql`

![screenshot](./images/mysql2.PNG)

Next we are gonna be installing php the final step ,we are going to be using the code `sudo apt install php libapache2-mod-php php-mysql` which is going to install three packages at once. To check if our installation is complete use code `php -v` to confirm the php version

At this point LAMP stack is fully operational, going to test the setup with a PHP script, to do that we are going to set up Apache Virtual Host to hold the website files and folders
creating a directory for the project with the command `sudo mkdir /var/www/projectlamp`

assign ownership to the current user ` sudo chown -R $USER:$USER /var/www/projectlamp`

create and open a new configuration file in Apache sites available using vi with the command `sudo vi /etc/apache2/sites-available/projectlamp.conf` save the file after making changes 

![screenshot](./images/php.PNG)

The above image shows how to enable the new virtual host using the a2ensite command now we reload Apache so the changes can take effect using the `sudo systemctl reload apache2`

The website is now active, but the web root /var/www/projectlamp is still empty. going to create an index.html file in that location so we can test that the virtual host works as expected using the command `sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html
`

Now we go to the website and check for our updates
succesful!!!
![screenshot](./images/apache.PNG)
succesful!!!

Next and final step is to enable php on our website, we need to edit the /etc/apache2/mods-enabled/dir.conf file we are gonna be using the command `sudo vim /etc/apache2/mods-enabled/dir.conf` after inputing the changes we are going to save and close the file. 

Now we need to reload apache so the changes can take effect using the command `sudo systemctl reload apache2`

Now we are going to create a new file name index.php to test that php is correctly installed using the command `vim /var/www/projectlamp/index.php.` This will open a blank file add the code `<?php
phpinfo();` which is valid php file, save the file and close the page 

Refresh the webpage 
Success!!! PhP installation is working as expected
![screenshot](./images/final.PNG)
Success!!! PhP installation is working as expected


Its best to remove the file we created its contains sensitive information to do this use the command `sudo rm /var/www/projectlamp/index.php`

We have now installed and implemented LAMP stack.













