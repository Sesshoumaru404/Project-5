IP address 52.11.159.100 and SSH  2200.

url: http://52.11.159.100/


### Software
[Apache][1]

[UFW][2]

[Glances][3]

[Fail2ban][4]

[Unattended_upgraes][5]

[Wsgi][6]

[Git][7]

[Virtualenv][8]

[Flask][9]

[PostgreSQL][10]

# Steps Taken:

### Create new user

Create a user:

`$ adduser <username> `

Grant sudo permission:

`$ mkdir /etc/sudoers.d`

Make a user file 

`$ touch /etc/sudoers.d/user`

Edit file to give username sudo persission

### Update all currently installed packages
Get the latest packages

`apt-get update`

Then upgrade system:

`apt get upgrade`

Use unattended-upgrades to auto updates

`apt-get install unattended-upgrades`

Then to enable:

`dpkg-reconfigure --priority=low unattended-upgrades`

To check log view /var/log/unattended-upgrades/unattended-upgrades.log

### Setup ssh

Create file 

`touch /.ssh/autrozed_keys`

To change ssh port open

`nano /etc/ssh/sshd_config`

Then edit lines to your configuration.

`sudo service ssh reload` to restart, then config UFW to block ports

Install Fail2ban, monitor login attempts:

`$ sudo apt-get install fail2ban`

Copy the default config file:

`$ sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local`

Edit config file to your liking:

`$ sudo vim /etc/fail2ban/jail.local`

### Set Time
Open the timezone config program:

`$ sudo dpkg-reconfigure tzdata`

### Install and configure Apache to serve a Python mod_wsgi application
Install Apache

`$ sudo apt-get install apache2`

Install mod_wsgi

`$ sudo apt-get install libapache2-mod-wsgi python-dev`

Enanble mod_wsgi

`$ sudo a2enmod wsgi`

### Setup Git
Install Git

`$ sudo apt-get install git`

Config Git

`$ git config --global user.name "YOUR NAME"`

`$ git config --global user.email "YOUR EMAIL ADDRESS"`

### App setup
Create no folder

`$ sudo mkdir /var/www/CatalogApp`

`$ cd /var/www/CatalogApp`

Clone you project 3 into folder

`git clone <project>`

`cd <project>`

Create a virtual environment for your app

`$ sudo apt-get install python-pip`

`$ sudo pip install virtualenv`

`$ sudo virtualenv venv`

Rename project.py to __init__.py this turns the folder into package

Get app working in virtual environment

`$ source venv/bin/activate`

Install needed packages

Create and edit Apache config file for new app

`$ sudo nano /etc/apache2/sites-available/catalog.conf`

Create and edit wsgi file

`$ sudo nano /var/www/CatalogApp/catalog.wsgi`

Restart Apache:

`$ sudo service apache2 restart`

# Third-party resources
[Digital ocean][11]

[Stackoverflow][12]

[Ubuntu documentation][13]

[1]: http://httpd.apache.org "Apache Homepage"
[2]: https://help.ubuntu.com/community/UFW "UFW Wiki"
[3]: http://nicolargo.github.io/glances/ "Glanes Homepage"
[4]: http://www.fail2ban.org/wiki/index.php/Main_Page "Fail2ban homepage"
[5]: https://help.ubuntu.com/community/AutomaticSecurityUpdates "Unattended_upgrades"
[6]: http://wsgi.readthedocs.org/en/latest/ "WSGI docs"
[7]: https://git-scm.com/ "Git homepage"
[8]: https://virtualenv.pypa.io/en/latest/ "Virtualenv"
[9]: http://flask.pocoo.org/ "Flask homepage"
[10]: http://www.postgresql.org/ "PostgreSQL Homepage"
[11]: https://www.digitalocean.com "Digital Ocean"
[12]: http://stackoverflow.com/ "StackOverFLow"
[13]: https://help.ubuntu.com/ "Ubuntu"