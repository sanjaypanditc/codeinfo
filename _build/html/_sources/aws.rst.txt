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
#. Go to Terminal and write below command (**Ubuntu**)
   ``ssh -i /web/yourkey.pem ec2-user@xxx.xxx.xxx.xxx``
#. Open PuttyGen software and load your pem file to generate ppk file.(**Windows**)
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
#. Search for allowoverrite None and replace it with allowoverrite All

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

Virtual Host Example
--------------------
.. code-block:: bash

	<VirtualHost *:80>
        ServerName aws.adopted.com
        #ServerName adopted.com
        #ServerAlias www.adopted.com
        DocumentRoot /var/www/adopted.com/public_html

        <Directory "/var/www/adopted.com/public_html">
                AllowOverride All
        </Directory>

        ErrorLog /var/log/httpd/adopted.com-error.log
        CustomLog /var/log/httpd/adopted.com-requests.log combined
	</VirtualHost>