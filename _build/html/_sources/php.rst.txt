.. _php:

PHP
============

Security Points
------------------
#. You are uploading the file use below code.
   ``$file = basename(realpath($_GET['file']));``
#. Avoid using mysql(i)_ extensions **use PDO**
   ``filter_var($_REQUEST['search'], FILTER_SANITIZE_FULL_SPECIAL_CHARS);``
#. use password_hash and password_verify
   ``$hash = password_hash($password, PASSWORD_DEFAULT);``
   ``password_verify($password, $hash);``
#. In php.ini change expose_php to Off
#. In php.ini change mail.add_x_header to Off
#. In php.ini change session.cookie_httponly to On
   ``session.cookie_httponly = On``
#. In php.ini change session.cookie_secure to On
   ``session.cookie_secure = On``
#. In php.ini change session.use_strict_mode to On
   ``session.use_strict_mode = 1``
#. allow_url_fopen = Off
   ``allow_url_include = Off``
#. In php.ini change open_basedir
   ``open_basedir = /var/www/html/``
   ``// Multiple directories can be specified with the ":" delimiter``
   ``open_basedir = /var/www/html/:/var/www/html2/:/var/www/html3/``
#. In php.ini change upload_temp_dir
   ``upload_tmp_dir = /var/www/html/tmp/``
   ``filter_var($email_address, FILTER_VALIDATE_EMAIL)``
#. ``filter_var($ip_address, FILTER_VALIDATE_IP)``
#. ``filter_var($url, FILTER_VALIDATE_URL)``
#. Don't Do This
   ``<a href="http://example.com" target="_blank">Click here</a>``
   Do This Instead
   ``<a href="https://example.com" target="_blank" rel="noopener noreferrer">Click here</a>``

SSL Redirection
---------------
.. code-block:: php

   ##Redirection to https file**
   RewriteCond %{HTTPS} off
   RewriteRule .* https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]

   ##Redirection to https and www page**
   RewriteCond %{HTTP_HOST} !^www\. [NC]
   RewriteRule .* https://www.%{HTTP_HOST}%{REQUEST_URI} [L,R=301]

Test
------------------