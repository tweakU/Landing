**Запускам CMS Wordpress на Ubuntu 24.04 (Angie + PHP-FPM)


** Установим Angie 
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

6) 
