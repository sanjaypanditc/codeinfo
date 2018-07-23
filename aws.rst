.. _digitalocean:

Introduction
============

lamp on aws with php7.2
-----------------------
1. Clink on launch a virtual machine  
2. Select "Amazon Linux 2 LTS Candidate AMI 2017.12.0" A latest Amazon linux candidate 64 bit.
3. Select "t2.micro" as Free tire instance.
4. Select auto option "Configure Instance Details"
5. Insert 30GB as storage.
6. Create security group and assign port.
7. Click on launch using a new key pair (Remember you need to put .pem file at secure place.)
8. Now your instance is ready.
**Ubuntu**
9. Go to Terminal and write below command
   ``ssh -i /web/yourkey.pem ec2-user@xxx.xxx.xxx.xxx``
**Windows**
10. Open PuttyGen software and load your pem file to generate ppk file.
11. ``sudo yum update -y``  
12. ``sudo yum install httpd``
13. ``sudo amazon-linux-extras install lamp-mariadb10.2-php7.2``  
14. ``sudo yum install -y mariadb-server php-mysqlnd``
15. ``sudo service httpd start``
16. ``sudo systemctl start httpd``
17. ``sudo systemctl enable httpd``  
18. ``sudo systemctl is-enabled httpd``
19. ``sudo systemctl start mariadb.service``
20. ``sudo systemctl enable mariadb.service`` 
21. ``mysql_secure_installation``
22. ``sudo yum -y install php-gd php-ldap php-odbc php-pear php-xml php-xmlrpc php-mbstring php-soap curl curl-devel``
23. ``sudo usermod -a -G apache ec2-user``
25. groups to know correct group.
26. ``sudo chown -R ec2-user:apache /var/www``
27. ``sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;``
28. ``find /var/www -type f -exec sudo chmod 0664 {} \;``

lamp on aws with php7.1
-----------------------
1. Clink on launch a virtual machine  
2. Select "Amazon Linux 2 LTS Candidate AMI 2017.12.0" A latest Amazon linux candidate 64 bit.
3. Select "t2.micro" as Free tire instance.
4. Select auto option "Configure Instance Details"
5. Insert 30GB as storage.
6. Create security group and assign port.
7. Click on launch using a new key pair (Remember you need to put .pem file at secure place.)
8. Now your instance is ready.
**Ubuntu**
9. Go to Terminal and write below command
   ``ssh -i /web/yourkey.pem ec2-user@xxx.xxx.xxx.xxx``
**Windows**
10. Open PuttyGen software and load your pem file to generate ppk file.
11. ``sudo yum update -y``  
12. ``sudo yum install httpd``