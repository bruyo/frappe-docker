# Frappe docker installation and set up

## STEP ONE: Installation of dependencies
RUN;
sudo apt-get install git

sudo apt-get install python3-dev

sudo apt-get install virtualenv

sudo apt install python3.10-venv

sudo apt-get install software-properties-common

sudo apt install mariadb-server

sudo mysql_secure_installation

## STEP TWO: MySQL database development files
RUN
sudo apt-get install libmysqlclient-dev

## STEP THREE: Edit the mariadb configuration (unicode character encoding)

sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf

In text editor input the following;

 [server]
 
 user = mysql
 
 pid-file = /run/mysqld/mysqld.pid
 
 socket = /run/mysqld/mysqld.sock
 
 basedir = /usr
 
 datadir = /var/lib/mysql
 
 tmpdir = /tmp
 
 lc-messages-dir = /usr/share/mysql
 
 bind-address = 127.0.0.1
 
 query_cache_size = 16M
 
 log_error = /var/log/mysql/error.log

 [mysqld]
 
 innodb-file-format=barracuda
 
 innodb-file-per-table=1
 
 innodb-large-prefix=1
 
 character-set-client-handshake = FALSE
 
 character-set-server = utf8mb4
 
 collation-server = utf8mb4_unicode_ci      
 
 [mysql]
 
 default-character-set = utf8mb4

Exit the text editor by clicking Ctrl X, type Y and ENTER

## STEP FOUR: Install other dependencies 

### Install Redis

RUN

sudo apt-get install redis-server

### Install Node.js 14.X package

RUN

sudo apt install curl 

curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash source ~/.profile

nvm install 14

### Install Yarn

sudo apt-get install npm

sudo npm install -g yarn

### Install wkhtmltopdf

sudo apt-get install xvfb libfontconfig wkhtmltopdf

## STEP FIVE: Install frappe-bench

RUN

sudo -H pip3 install frappe-bench==5.10.1

bench --version

## STEP SIX: Initilise the frappe bench & install frappe latest version





