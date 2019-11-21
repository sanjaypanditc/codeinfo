Htaccess
##########

SSL Redirection
---------------
.. code-block:: bash

   ##Redirection to https file**
   RewriteCond %{HTTPS} off
   RewriteRule .* https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]

   ##Redirection to https and www page**
   RewriteCond %{HTTP_HOST} !^www\. [NC]
   RewriteRule .* https://www.%{HTTP_HOST}%{REQUEST_URI} [L,R=301]

Test
------------------