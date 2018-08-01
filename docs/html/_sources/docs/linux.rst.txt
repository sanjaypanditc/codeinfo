.. _linux:

Linux
============

Commands
--------
* ``grep keyword /var/spool/cron/root | egrep -v ^# | grep -v ^$ | awk '{print $1,$2,$3,$4,$5,$8}'``
* ``cat netstat.log.5 |  awk '$4 ~ /:80$/ {c++;print $5 | "sed 's/::ffff://' | sed 's/:.*$//'| sort | uniq -c | sort -n | tail -n 10"} END {print c}'``
* ``netstat -plantu | grep -c :1433``
* ``ifconfig eth0 ``

* **Print last 20 lines from the error_log file** ``tail -20   /var/log/httpd/error_log``
* **Get max number of client on apache configuration** ``grep -i maxclients /etc/httpd/conf/httpd.conf``
* ``cat /etc/my.cnf  | grep cache -i | grep -v ^#``
* ``grep "^|" queries-pre-restart.txt | awk '{ print $14 }' | sort | uniq -c | sort -nr``
*  **Will make directory at nested level (it will create both directory)** ``mkdir -p www/public_html``

* **To compress all files of foldername** ``tar -cvzf docs.tar.gz /var/www/html/foldername``
* **extract docs.tar.gz in docs folder** ``tar -xvzf docs.tar.gz``