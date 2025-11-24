## Запускам CMS Wordpress на Ubuntu 24.04 (Angie + PHP-FPM)


**Установим Angie**  
[Официальная документацияю. Пакетная установка Angie](https://angie.software/angie/docs/installation/oss_packages/#angie-install-deb-oss)

1) Установите вспомогательные пакеты для подключения репозитория Angie:
```console
 sudo apt-get update
 sudo apt-get install -y ca-certificates curl
```

2) Скачайте открытый ключ репозитория Angie для проверки подлинности пакетов:
```console
 sudo curl -o /etc/apt/trusted.gpg.d/angie-signing.gpg \
            https://angie.software/keys/angie-signing.gpg
```

3) Подключите репозиторий Angie:
```console
 echo "deb https://download.angie.software/angie/$(. /etc/os-release && echo "$ID/$VERSION_ID $VERSION_CODENAME") main" \
    | sudo tee /etc/apt/sources.list.d/angie.list > /dev/null
```

4) Обновите индексы репозиториев:
```console
 sudo apt-get update
```

5) Установите пакет Angie:
```console
 sudo apt-get install -y angie
```

!) Проверим работоспособность сервиса:
```console
funt1k@http:~$ sudo systemctl status angie.service
● angie.service - Angie - high performance web server
     Loaded: loaded (/usr/lib/systemd/system/angie.service; enabled; preset: enabled)
     Active: active (running) since Mon 2025-11-24 12:49:27 UTC; 31s ago
       Docs: https://en.angie.software/angie/docs/
    Process: 2134 ExecStart=/usr/sbin/angie -c /etc/angie/angie.conf (code=exited, status=0/SUCCESS)
   Main PID: 2135 (angie)
      Tasks: 3 (limit: 4603)
     Memory: 57.3M (peak: 57.3M)
        CPU: 162ms
     CGroup: /system.slice/angie.service
             ├─2135 "angie: master process v1.10.3 #1 [/usr/sbin/angie -c /etc/angie/angie.conf]"
             ├─2136 "angie: worker process #1"
             └─2137 "angie: worker process #1"

Nov 24 12:49:26 http systemd[1]: Starting angie.service - Angie - high performance web server...
Nov 24 12:49:27 http systemd[1]: Started angie.service - Angie - high performance web server.

funt1k@http:~$ sudo ss -ntlp | grep 80
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("angie",pid=2137,fd=6),("angie",pid=2136,fd=6),("angie",pid=2135,fd=6))
```


**Установим дополнительные пакеты (php, mysql etc):
```console
 sudo apt install php8.3 php8.3-fpm php8.3-mysql mysql-server-8.0 php-curl php-gd php-intl php-mbstring php-soap php-xml php-xmlrpc php-zip
```
