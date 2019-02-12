.. _php:

PHP
============

Security Points
------------------
* Avoid using mysql(i)_ extensions **use PDO**
* You should use below code at the time uploading file.

   ``$file = basename(realpath($_GET['file']));``
* SANITIZE user data

   ``filter_var($_REQUEST['search'], FILTER_SANITIZE_FULL_SPECIAL_CHARS);``
* use password_hash and password_verify

   ``$hash = password_hash($password, PASSWORD_DEFAULT);``
   ``password_verify($password, $hash);``
* In php.ini change expose_php to Off
* In php.ini change mail.add_x_header to Off
* In php.ini change session.cookie_httponly to On

   ``session.cookie_httponly = On``
* In php.ini change session.cookie_secure to On

   ``session.cookie_secure = On``
* In php.ini change session.use_strict_mode to On

   ``session.use_strict_mode = 1``
* allow_url_fopen = Off

   ``allow_url_include = Off``
* In php.ini change open_basedir

   ``open_basedir = /var/www/html/``
   ``// Multiple directories can be specified with the ":" delimiter``
   ``open_basedir = /var/www/html/:/var/www/html2/:/var/www/html3/``
* In php.ini change upload_temp_dir

   ``upload_tmp_dir = /var/www/html/tmp/``
   ``filter_var($email_address, FILTER_VALIDATE_EMAIL)``

* ``filter_var($ip_address, FILTER_VALIDATE_IP)``
* ``filter_var($url, FILTER_VALIDATE_URL)``
* Don't Do This

   ``<a href="http://example.com" target="_blank">Click here</a>``
   Do This Instead
   
   ``<a href="https://example.com" target="_blank" rel="noopener noreferrer">Click here</a>``

**Generate PHP Error on a Specific IP** Generate PHP Errors on a Specific IP

.. code-block:: bash

   if($_SERVER["REMOTE_ADDR"] =='xxx.xxxx.xxx.xxx'){
     error_reporting(E_ALL);
      ini_set('display_errors','Off');
      ini_set("log_errors", 1);
      ini_set("error_log", "D:/xampp/htdocs/live/errors/lservererror.html");
   }

**Write a PHP File** Write PHP Errors in a single file

.. code-block:: bash

   ##Generate file##
   $arrayInfo =array();
   $path = "/var/www/html/";
   $fp = fopen($path."arrayDetails.txt", "a");
   fwrite($fp, print_r($arrayInfo,true));
   fclose($fp);