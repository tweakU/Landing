## [MySQL Репликация](https://my.rebrainme.com/video/1358?course=podpiska-linux)


1) Установим MySQL Server 8.0:
```console
root@mysql-slave:~# apt install mysql-server-8.0 -y
```

```console
root@http:~# mysql
CREATE DATABASE wordpress_db;
CREATE USER 'wp_user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL ON wordpress_db.* TO 'wp_user'@'localhost';
exit

SHOW DATABASES;
SELECT user,host FROM mysql.user;
SHOW MASTER STATUS \G
CHANGE MASTER TO MASTER_HOST='192.168.1.8', MASTER_USER='slave', MASTER_PASSWORD='password', MASTER_LOG_FILE='binlog.000006', MASTER_LOG_POS=470;
SHOW SLAVE STATUS \G
STOP SLAVE; (to edit)
CREATE DATABASE %db_name; (to change binlog pos)
DROP DATABASE %db_name;
RESET SLAVE ALL; (flush slave)

Debuging:
ALTER USER 'slave'@'%' IDENTIFIED WITH mysql_native_password BY 'qwerty'; FLUSH PRIVILEGES;
GRANT REPLICATION SLAVE, REPLICATION CLIENT ON *.* TO 'slave'@'%' IDENTIFIED BY 'qwerty'; FLUSH PRIVILEGES;
```
