## [MySQL Репликация](https://my.rebrainme.com/video/1358?course=podpiska-linux)


1) Установите вспомогательные пакеты для подключения репозитория Angie:
```console

```


root@http:/var/www/html/wordpress# mysql
CREATE DATABASE wordpress_db;
CREATE USER 'wp_user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL ON wordpress_db.* TO 'wp_user'@'localhost';
exit

