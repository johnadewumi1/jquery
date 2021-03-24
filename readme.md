# A front-end only toDo App 
## Purpse: Simple front-end app for AWS deployment course students.

### Overview
Anything but elegant, it's nothing but Javascript, jQuery, HTML, CSS and a bit of frustration as I forgot how hard it is to live without state management the past several years. Requires as little web dev understanding as possible. 

It is the bones of the [materialize css](http://materializecss.com/) starter theme. 

### Technologies Used
* Front-end only
* jQuery
* materializecss
* localStorage

### Notes
The code is heavily commented and follows a very basic procedural structure. jQuery listeners stand in place of native JS listeners as more people are familiar with jQuery selection syntax


### Apache on Ubuntu 18.04 LTS (bionic) ###

#SSH into the server
#SSH into the server running your HTTP website as a user with sudo privileges.

Install snapd
#You'll need to install snapd and make sure you follow any instructions to enable classic snap support.
#Follow these instructions on snapcraft's site to install snapd.

--install snapd

#Ensure that your version of snapd is up to date
#Execute the following instructions on the command line on the machine to ensure that you have the latest version of snapd.

--sudo snap install core; sudo snap refresh core
#Remove certbot-auto and any Certbot OS packages
#If you have any Certbot packages installed using an OS package manager like apt, dnf, or yum, you should 
#remove them before installing the Certbot snap to ensure that when you run the command certbot the snap is used rather than the installation from your OS package manager. 
#The exact command to do this depends on your OS, but common examples are 
--sudo apt-get remove certbot, sudo dnf remove certbot, or sudo yum remove certbot.

#If you previously used Certbot through the certbot-auto script, you should also remove its installation by following the instructions here.

#Install Certbot
#Run this command on the command line on the machine to install Certbot.

--sudo snap install --classic certbot
#Prepare the Certbot command
#Execute the following instruction on the command line on the machine to ensure that the certbot command can be run.

--sudo ln -s /snap/bin/certbot /usr/bin/certbot
#Choose how you'd like to run Certbot
#Either get and install your certificates...
#Run this command to get a certificate and have Certbot edit your Apache configuration automatically to serve it, turning on HTTPS access in a single step.

--sudo certbot --apache
#Or, just get a certificate
#If you're feeling more conservative and would like to make the changes to your Apache configuration by hand, run this command.

--sudo certbot certonly --apache

#Test automatic renewal
#The Certbot packages on your system come with a cron job or systemd timer that will renew your certificates automatically before they expire. 
#You will not need to run Certbot again, unless you change your configuration. You can test automatic renewal for your certificates by running this command:

--sudo certbot renew --dry-run
#The command to renew certbot is installed in one of the following locations:

/etc/crontab/
/etc/cron.*/*
systemctl list-timers
#Confirm that Certbot worked
#To confirm that your site is set up properly, visit https://yourwebsite.com/ in your browser and look for the lock icon in the URL bar.

## Commands from initial SSH ##

$ sudo apt update
$ clear
$ sudo apt install apache2
$ cd /etc/apache2/sites-available/
$ clear
$ ls
$ sudo vi ridiculous-inc.com.conf
$ cd /var/www
$ sudo git clone https://github.com/ridiculous-ijquery-todo.git ridic
$ sudo a2ensite ridiculous-inc.com.conf 
$ sudo service apache2 restart
$ sudo apt-get update
$ clear
$ sudo apt-get install software-properties-common
$ sudo add-apt-repository ppa:certbot/certbot
$ clear
$ sudo apt-get update
$ sudo apt-get install python-certbot-apache 
$ clear
$ sudo certbot --apache
$ history


## VirtualHost for .com.conf file ##

<virtualhost *:80="">
    DocumentRoot /var/www/ridic
    ServerName ridiculous-inc.com
    <directory "="" var="" www="" ridic"="">
        allow from all
        AllowOverride All
        Order allow,deny
        Options +Indexes
    </directory>
</virtualhost>