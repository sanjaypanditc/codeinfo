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
Please visit [LowendBox](https://lowendbox.com/blog/how%E2%80%8B-%E2%80%8Bto%E2%80%8B-%E2%80%8Bfix%E2%80%8B-%E2%80%8Ba%E2%80%8B-%E2%80%8Bmysql%E2%80%8B-%E2%80%8Bfailed%E2%80%8B-%E2%80%8Bto%E2%80%8B-%E2%80%8Bstart%E2%80%8B-%E2%80%8Berror/)