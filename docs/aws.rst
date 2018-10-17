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

** Start Below commands**

#. ``sudo yum update -y``  
#. ``sudo yum install httpd``
#. ``sudo amazon-linux-extras install lamp-mariadb10.2-php7.2``  
#. ``sudo yum install -y mariadb-server php-mysqlnd``
#. ``sudo service httpd start``
#. ``sudo systemctl start httpd``
#. ``sudo systemctl enable httpd``  
#. ``sudo systemctl is-enabled httpd``
#. ``sudo systemctl start mariadb.service``
#. ``sudo systemctl enable mariadb.service`` 
#. ``mysql_secure_installation``
#. ``sudo yum -y install php-gd php-ldap php-odbc php-pear php-xml php-xmlrpc php-mbstring php-soap curl curl-devel``
#. ``sudo usermod -a -G apache ec2-user``
#. groups to know correct group.
#. ``sudo chown -R ec2-user:apache /var/www``
#. ``sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;``
#. ``find /var/www -type f -exec sudo chmod 0664 {} \;``
#. Enable Mode rewrite
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
#. ``sudo yum install httpd``

Initial Setup
-------------
**Connect to server**
``ssh -i pathof pem file serveruser@yourip``
**Create User**
``sudo adduser username``
**SetPassword**
``sudo passwd username``
it will ask for insert SetPassword, you need to put your desire password.
**Set Directory Path of that user**
``sudo usermod -d /var/www/html/ username``
**

Mysql Initial
~~~~~~~~~~~~~
**First logged in Mysql panel**
**Adduser and provide permission**
``CREATE USER 'mysqlusername'@'%' IDENTIFIED BY 'mysqluserpassword';``
``GRANT ALL PRIVILEGES ON *.* TO 'rsmaauusr'@'%' WITH GRANT OPTION;``
``EATE USER 'ankit'@'%' IDENTIFIED WITH mysql_native_password AS '***';``
``GRANT ALL PRIVILEGES ON *.* TO 'ankit'@'%' REQUIRE NONE WITH GRANT OPTION MAX_QUERIES_PER_HOUR 0 MAX_CONNECTIONS_PER_HOUR 0 MAX_UPDATES_PER_HOUR 0 MAX_USER_CONNECTIONS 0;``
``GRANT ALL PRIVILEGES ON `adopted`.* TO 'ankit'@'%' WITH GRANT OPTION;``


devadt	Kt1V!bi^CNFU


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

Generate PPK file
--------------------
* Download Puttygen software from this `link <https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html>`_
* Install it 
* Click on Conversion Tab
* Upload your .pem file
* Click on *Save Private key* to generate PPK file.