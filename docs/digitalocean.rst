.. _digitalocean:

Digital Ocean
==============

## Ubuntu ##

You may be using a ubuntu machine or you are creating virtual host on ubuntu server.
Open terminal using ctrl+alt+T in ubuntu, putty on windows. Connect with ssh if you are going to creating virtual host on ubuntu server.

1. sudo apt-get update  (it will update all system libraries)
2. cd /var/www          (Move to www path)
3. sudo mkdir -p example1.com/public_html    (it will create both directory example1.com and example1.com/public_html)
4. sudo mkdir -p example2.com/public_html    (it will create both directory example2.com and example2.com/public_html)
5. cd /etc/apache2/sites-available/
6. sudo cp 000-default.conf example1.com.conf
7. sudo cp 000-default.conf example2.com.conf
8. nano example1.com.conf and put below code in it

```
<VirtualHost *:80>
ServerAdmin webmaster@example1.com
ServerName example1.com
ServerAlias www.example1.com
DocumentRoot /var/www/example1.com/public_html
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

9. nano example2.com.conf and put below code in it

```
<VirtualHost *:80>
ServerAdmin webmaster@example1.com
ServerName example2.com
ServerAlias www.example2.com
DocumentRoot /var/www/example2.com/public_html
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

10. sudo a2dissite 000-default.conf
11. sudo a2ensite example1.com.conf
12. sudo a2ensite example2.com.conf
13. sudo systemctl restart apache2
14. cd /var/www
15. nano example1.com/public_html/index.html and put "Welcome to example1.com"
16. nano example2.com/public_html/index.html and put "Welcome to example2.com"
17. now you need to make host entries to your local machines.
18. on ubuntu you need to open /etc/hosts file and make host entry like, Use C:\Windows\System32\drivers\etc\hosts if you are on windows
19. xxx.xxx.xxx.xxx example1.com

    xxx.xxx.xxx.xxx www.example1.com
    
    xxx.xxx.xxx.xxx example2.com
    
    xxx.xxx.xxx.xxx www.example2.com

Now your subdomains/virtual host are ready.