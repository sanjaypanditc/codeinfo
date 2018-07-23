.. _php:

Introduction
============

Security Points
------------------
1. you are uploading the file use below code.
$file = basename(realpath($_GET['file']));

2. Avoid using mysql(i)_ extensions
use PDO

3. filter_var($_REQUEST['search'], FILTER_SANITIZE_FULL_SPECIAL_CHARS);

4. use password_hash and password_verify
$hash = password_hash($password, PASSWORD_DEFAULT);
password_verify($password, $hash);

5.In php.ini change expose_php to Off
6.In php.ini change mail.add_x_header to Off
7.In php.ini change session.cookie_httponly to On
session.cookie_httponly = On

8.In php.ini change session.cookie_secure to On
session.cookie_secure = On

9.In php.ini change session.use_strict_mode to On
session.use_strict_mode = 1

10.allow_url_fopen = Off
allow_url_include = Off

11. In php.ini change open_basedir
open_basedir = /var/www/html/

// Multiple directories can be specified with the ":" delimiter
open_basedir = /var/www/html/:/var/www/html2/:/var/www/html3/

12. In php.ini change upload_temp_dir
upload_tmp_dir = /var/www/html/tmp/

13. filter_var($email_address, FILTER_VALIDATE_EMAIL)
14. filter_var($ip_address, FILTER_VALIDATE_IP)
15. filter_var($url, FILTER_VALIDATE_URL)

16. Don't Do This
<a href="http://example.com" target="_blank">Click here</a>

Do This Instead
<a href="https://example.com" target="_blank" rel="noopener noreferrer">Click here</a>

Shortcut keys
-------------


A word about users
------------------