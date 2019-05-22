.. _aws:

AWS
============
Amazon Web service is well known service provider in cloud industry, which provides various services to use in this industry.

Install lamp with php7.2
------------------------
#. Clink on launch a virtual machine  
#. Select "Amazon Linux 2 LTS Candidate AMI 2017.12.0" A latest Amazon linux candidate 64 bit.
#. Select "t2.micro" as Free tire instance.
#. Select auto option "Configure Instance Details"
#. Insert 30GB as storage.
#. Create security group and assign port.
#. Click on launch using a new key pair (Remember you need to put .pem file at secure place.)
#. Now your instance is ready.

.. Tip::

   **Ubuntu users** Open Terminal and write below command
   ``ssh -i /web/yourkey.pem ec2-user@xxx.xxx.xxx.xxx``

   **Windows users** generate PPK file and use it in Putty

**Start Below commands**

#. ``sudo yum update -y``  
#. ``sudo amazon-linux-extras install -y lamp-mariadb10.2-php7.2 php7.2``
#. ``sudo yum -y install php-mysqlnd php-gd php-ldap php-odbc php-pear php-xml php-xmlrpc php-mbstring php-soap curl curl-devel php-intl``
#. ``sudo yum install -y httpd mariadb-server``
#. ``sudo usermod -a -G apache ec2-user``
#. ``sudo chown -R ec2-user:apache /var/www``
#. ``sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;``
#. ``find /var/www -type f -exec sudo chmod 0664 {} \;``
#. ``sudo service httpd start``
#. ``sudo systemctl start httpd``
#. ``sudo systemctl enable httpd``  
#. ``sudo systemctl is-enabled httpd``
#. ``sudo systemctl start mariadb.service``
#. ``sudo systemctl enable mariadb.service``
#. ``mysql_secure_installation``
#. ``cd /etc/httpd/conf``
#. ``nano httpd.conf``
#. Search for allowoverride None and replace it with allowoverride All

Install lamp with php7.1
------------------------
#. Clink on launch a virtual machine  
#. Select "Amazon Linux 2 LTS Candidate AMI 2017.12.0" A latest Amazon linux candidate 64 bit.
#. Select "t2.micro" as Free tire instance.
#. Select auto option "Configure Instance Details"
#. Insert 30GB as storage.
#. Create security group and assign port.
#. Click on launch using a new key pair (Remember you need to put .pem file at secure place.)
#. Now your instance is ready.
#. Go to Terminal and write below command (**Ubuntu**)
   ``ssh -i /web/yourkey.pem ec2-user@xxx.xxx.xxx.xxx``
#. Open PuttyGen software and load your pem file to generate ppk file.(**Windows**)
#. ``sudo yum update -y``  
#. ``sudo yum install -y httpd24``
#. ``sudo service httpd start``
#. ``sudo chkconfig httpd on``
#. ``sudo yum install -y mysql-server``
#. ``sudo service mysqld start``
#. ``sudo chkconfig mysqld on``
#. ``sudo yum install php71``
#. ``sudo yum -y install php71-gd php71-ldap php71-odbc php71-pear php71-xml php71-xmlrpc php71-mbstring php71-soap curl curl-devel``
#. ``sudo usermod -a -G apache ec2-user``
#. groups to know correct group.
#. ``sudo chown -R ec2-user:apache /var/www``
#. ``sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;``
#. ``find /var/www -type f -exec sudo chmod 0664 {} \;``
#. ``mysql_secure_installation``
#. Enable Mode rewrite
#. ``cd /etc/httpd/conf``
#. ``nano httpd.conf``
#. Search for allowoverride None and replace it with allowoverride All


Extras
-------

Create user
~~~~~~~~~~~~~~
**Connect to server**
``ssh -i pathof pem file serveruser@yourip``
**Create User**
``sudo adduser username``
**SetPassword**
``sudo passwd username``
it will ask for insert SetPassword, you need to put your desire password.
**Set Directory Path of that user**
``sudo usermod -d /var/www/html/ username``

Mysql Initial
~~~~~~~~~~~~~
**First logged in Mysql panel**
**Adduser and provide permission**
``CREATE USER 'mysqlusername'@'%' IDENTIFIED BY 'mysqluserpassword';``
``GRANT ALL PRIVILEGES ON *.* TO 'rsmaauusr'@'%' WITH GRANT OPTION;``
``EATE USER 'ankit'@'%' IDENTIFIED WITH mysql_native_password AS '***';``
``GRANT ALL PRIVILEGES ON *.* TO 'ankit'@'%' REQUIRE NONE WITH GRANT OPTION MAX_QUERIES_PER_HOUR 0 MAX_CONNECTIONS_PER_HOUR 0 MAX_UPDATES_PER_HOUR 0 MAX_USER_CONNECTIONS 0;``
``GRANT ALL PRIVILEGES ON `adopted`.* TO 'ankit'@'%' WITH GRANT OPTION;``

TimeZone change
~~~~~~~~~~~~~~~
``ls -l /etc/localtime``
``cp /etc/localtime /root/old.timezone``
``rm /etc/localtime``
``ln -s /usr/share/zoneinfo/US/Pacific /etc/localtime``


vsftpd install
~~~~~~~~~~~~~~
``pasv_enable=YES``
``pasv_min_port=1024``
``pasv_max_port=1048``
``pasv_address=<Public IP of your instance>``


Virtual Host Example
--------------------
.. code-block:: bash

    <VirtualHost *:80>
        ServerName www.xyz.com
        ServerAlias www.xyz.com
        ServerAdmin youremailaddress
        DocumentRoot /var/www/xyz.com/public_html

        <Directory "/var/www/xyz.com/public_html">
                AllowOverride All
        </Directory>

        ErrorLog /var/log/httpd/xyz.com-error.log
        CustomLog /var/log/httpd/xyz.com-requests.log combined
    </VirtualHost>