.. _linux:

Linux
============

Commands
--------
* ``grep keyword /var/spool/cron/root | egrep -v ^# | grep -v ^$ | awk '{print $1,$2,$3,$4,$5,$8}'``
* ``cat netstat.log.5 |  awk '$4 ~ /:80$/ {c++;print $5 | "sed 's/::ffff://' | sed 's/:.*$//'| sort | uniq -c | sort -n | tail -n 10"} END {print c}'``
* ``netstat -plantu | grep -c :1433``
* ``ifconfig eth0``
* **Print last 20 lines from the error_log file**
  ``tail -20   /var/log/httpd/error_log``
* **Get max number of client on apache configuration**
  ``grep -i maxclients /etc/httpd/conf/httpd.conf``
* ``cat /etc/my.cnf  | grep cache -i | grep -v ^#``
* ``grep "^|" queries-pre-restart.txt | awk '{ print $14 }' | sort | uniq -c | sort -nr``
* **Will make directory at nested level (it will create both directory)**
  ``mkdir -p www/public_html``
* **To compress all files of foldername**
  ``tar -cvzf docs.tar.gz /var/www/html/foldername``
* **extract docs.tar.gz in docs folder**
  ``tar -xvzf docs.tar.gz``
* **Symlink specific time on server**
  ``sudo ln -s /usr/share/zoneinfo/US/Pacific /etc/localtime``


Cronjobs
--------
.. code-block:: bash

	# Example of job definition:
	# .---------------- minute (0 - 59)
	# |  .------------- hour (0 - 23)
	# |  |  .---------- day of month (1 - 31)
	# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
	# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
	# |  |  |  |  |
	# *  *  *  *  * user-name command to be executed

	#crontab -e
	*/10 *  *  *  * wget -O /dev/null webpage url
	0    *  *  *  * /usr/bin/php /var/www/html/projectname/yourphpfile

	#cronjob for last day of month
	[ "$(/bin/date +\%d -d tomorrow)" = "01" ] && /usr/local/bin/php /var/www/html/projectname/yourphpfile