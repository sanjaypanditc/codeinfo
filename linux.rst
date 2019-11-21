.. _linux:

Linux
============

Commands
---------
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
* **search text from file name**
	``grep word /mnt/data/filepath``
* **Mount a Drive**
	``sudo mount /dev/xvdf /mnt/data/``
* **UnMount a Drive**
	``sudo umount --verbose /mnt/data/``
* **Blank an email**
	``> /var/spool/mail/root``


.. Tip::

  ``cd /tmp``
  ``curl -sS https://getcomposer.org/installer | php``
  ``Move it to /usr/local/bin/``
  ``mv composer.phar /usr/local/bin/composer``



logCommands
-----------

.. code-block::bash

	awk '{print $1}' combined_log         # ip address (%h)
	awk '{print $2}' combined_log         # RFC 1413 identity (%l)
	awk '{print $3}' combined_log         # userid (%u)
	awk '{print $4,5}' combined_log       # date/time (%t)
	awk '{print $9}' combined_log         # status code (%>s)
	awk '{print $10}' combined_log        # size (%b)

	You might notice that we've missed out some items. To get to them we need to set the delimiter to the " character which changes the way the lines are 'exploded' and allows the following:
	awk -F\" '{print $2}' combined_log    # request line (%r)
	awk -F\" '{print $4}' combined_log    # referer
	awk -F\" '{print $6}' combined_log    # user agent


	###awk -F\" '{print $4,5}' '{print $4}' combined_log requests.log

	awk '{print $9}' requests.log | sort | uniq -c | sort
	awk '{print $1}' requests.log | sort | uniq -c | sort -r -n | head -n 10


	awk -F\" '{print $6}' requests.log | sort | uniq -c | sort   (number of browsers request)

	awk -F\" '($6 ~ /^-?$/)' requests.log | awk '{print $1}' | sort -r -n | uniq

	awk -F\" '($6 ~ /^-?$/)' requests.log | awk '{print $1}' | sort -r -n | uniq

	awk -F\" '{print $6}' requests.log \
	  | sed 's/(\([^;]\+; [^;]\+\)[^)]*)/(\1)/' \
	  | awk '{print $1}' | uniq -c | sort -r -n | head -n 10

	awk -F\" '{print $6}' /var/log/httpd/requests.log   | awk '{print $1}' | sort -r -n | uniq -c | sort -r -n | head -n 10

	awk -F\" '($6 ~ /^-?$/)' requests.log | awk '{print $1}' | sort -r -n | uniq -c | sort -r -n | head -n 10

	grep 12/Aug requests.log | grep state | \
	awk '{ print $1 }' |  sort -n | uniq -c | \
	sort -rn | head -n 10


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



Generate PPK file
--------------------
* Download Puttygen software from this `link <https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html>`_
* Install it 
* Click on Conversion Tab
* Upload your .pem file
* Click on *Save Private key* to generate PPK file.