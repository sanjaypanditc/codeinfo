.. _mysql:

MySQL
============

**Convert DateTime in UnixTimeStamp**  
``SELECT *,from_unixtime(date_added) FROM `TABLE_NAME`  order by date_added desc``

**Space consume by a table**  
``SELECT table_schema "Data Base Name",sum( data_length + index_length ) / 1024 / 1024 /1024 "Used GB" FROM information_schema.TABLES GROUP BY table_schema ;``

**Character Set** 
``utf8mb4_unicode_ci``

**Set a login path using terminal/putty**  
``mysql_config_editor set --login-path=anyname  --host=localhost --port=3306 --socket=/var/run/mysqld/mysqld.sock --user=databaseuser --password``

**How to fix a MySQL Failed to Start error**  
Please visit `LowendBox <https://lowendbox.com/blog/how%E2%80%8B-%E2%80%8Bto%E2%80%8B-%E2%80%8Bfix%E2%80%8B-%E2%80%8Ba%E2%80%8B-%E2%80%8Bmysql%E2%80%8B-%E2%80%8Bfailed%E2%80%8B-%E2%80%8Bto%E2%80%8B-%E2%80%8Bstart%E2%80%8B-%E2%80%8Berror/>`_

**Give Permission to mysqluser** 

.. code-block:: bash

	CEATE USER 'ankit'@'%' IDENTIFIED WITH mysql_native_password AS '***';
	GRANT ALL PRIVILEGES ON *.* TO 'ankit'@'%' REQUIRE NONE WITH GRANT OPTION MAX_QUERIES_PER_HOUR 0 MAX_CONNECTIONS_PER_HOUR 0 MAX_UPDATES_PER_HOUR 0 MAX_USER_CONNECTIONS 0;
	GRANT ALL PRIVILEGES ON `adopted`.* TO 'ankit'@'%' WITH GRANT OPTION;

Mysql Backup/Restore
--------------------
.. code-block:: bash

	Download full database (.gz extention)  
	mysqldump -h[host] -u[user] -p[password] [database] | gzip -c | cat > /var/www/html/mysqldump_[database]_$(date +%Y%m%d_%H%M%S).sql.gz

	Download full database with ssl enabled (.gz extention)  
	mysqldump -h[host] -u[user] -p[password] [database] --ssl-ca=[.PEM file] [database] | gzip -c | cat > /var/www/html/mysqldump_[database]_$(date +%Y%m%d_%H%M%S).sql.gz

	Download Specific database table (.gz extention)  
	mysqldump -h[host] -u[user] -p[password] [database] [tablename] | gzip -c | cat > /var/www/html/mysqldump_[database]_[tablename]_$(date +%Y%m%d_%H%M%S).sql.gz

	Download Database after ignore some table (.gz extention)**  
	mysqldump -h[host] -u[user] -p[password] [database] --ignore-table=[table1] --ignore-table=[table2]| gzip -c | cat > /var/www/html/mysqldump_[database]_$(date +%Y%m%d_%H%M%S).sql.gz

	Restore Backup file in Database  
	mysql -h[host] -u[user] -p[password] [database] < /var/www/html/database.sql

	Restore Database using .sql.gz file with ssl enabled  
	zcat database.sql.gz | mysql -h[host] -u[user] -p[password] --ssl-ca=[.PEM file] [database]

	Restore Database using .sql.gz file  
	zcat database.sql.gz | mysql -h[host] -u[user] -p[password] [database]