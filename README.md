## Configure Remote Access To MariaDB Databases:
- enable remote access: `sudo vim /etc/mysql/mariadb.conf.d/50-server.cnf`
- change bind-address row to: `bind-address = 0.0.0.0`
- After making the change above: `sudo systemctl restart mysql.service` and `sudo systemctl restart mariadb.service`
- verify that the change happens: `sudo netstat -anp | grep 3306`
- enable a client to connect to a database, you must grant access to the remote server:
`GRANT ALL ON wpdatabase.* TO 'wpuser'@'3.17.133.111' IDENTIFIED BY 'new password here';`
- connect to the database from the remote: `sudo mysql -u wpuser -h 3.17.130.111 -ppass1234 wpdatabase;`

see: https://websiteforstudents.com/configure-remote-access-mysql-mariadb-databases/