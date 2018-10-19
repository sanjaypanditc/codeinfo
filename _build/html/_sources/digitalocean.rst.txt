.. _digitalocean:

Digital Ocean
==============

Install Ubuntu
--------------

Open terminal using ctrl+alt+T in ubuntu, putty on windows. Connect with ssh if you are going to creating virtual host on ubuntu server.

* sudo apt-get update  (it will update all system libraries)
* cd /var/www          (Move to www path)
* sudo mkdir -p example1.com/public_html    (it will create both directory example1.com and example1.com/public_html)
* sudo mkdir -p example2.com/public_html    (it will create both directory example2.com and example2.com/public_html)
* cd /etc/apache2/sites-available/
* sudo cp 000-default.conf example1.com.conf
* sudo cp 000-default.conf example2.com.conf
* nano example1.com.conf and put below code in it

.. code:: bash

	<VirtualHost *:80>
	ServerAdmin webmaster@example1.com
	ServerName example1.com
	ServerAlias www.example1.com
	DocumentRoot /var/www/example1.com/public_html
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
	</VirtualHost>

* ``nano example2.com.conf`` and put below code in it

.. code:: bash

	<VirtualHost *:80>
	ServerAdmin webmaster@example1.com
	ServerName example2.com
	ServerAlias www.example2.com
	DocumentRoot /var/www/example2.com/public_html
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
	</VirtualHost>

* ``sudo a2dissite 000-default.conf``
* ``sudo a2ensite example1.com.conf``
* ``sudo a2ensite example2.com.conf``
* ``sudo systemctl restart apache2``
* ``cd /var/www``
* ``nano example1.com/public_html/index.html`` and put "Welcome to example1.com"
* ``nano example2.com/public_html/index.html`` and put "Welcome to example2.com"
* now you need to make host entries to your local machines.
* on ubuntu you need to open ``/etc/hosts`` file and make host entry like, Use ``C:\Windows\System32\drivers\etc\hosts`` if you are on windows
* xxx.xxx.xxx.xxx example1.com
  xxx.xxx.xxx.xxx www.example1.com
  xxx.xxx.xxx.xxx example2.com
  xxx.xxx.xxx.xxx www.example2.com
  Now your subdomains/virtual host are ready.