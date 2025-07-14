---
title: Запуск проекта локально с возможностью авторизации через Smart ID
type: docs
weight: 7
---

## ⚡️ Запуск проекта локально с возможностью авторизации через Smart ID

### Потребуется:
- Рабочий VPN (NGate) и аккаунт в smart-stage.mos.ru
- Локально установленный и запущенный Nginx (для проксирования нужных запросов)
- Node.js для запуска проекта через server.js
- Сертификаты для запуска проекта локально на https (браузер будет ругаться на недоверенный сертификат, но это нормально)

### Конфигурация Nginx:
Для проксирования запросов нужно обработать 2 location, один из которых проксирует запрос на локально запущенный фронт (/), а второй на сервис smart-stage.mos.ru для авторизации (/auth/user)
Пример конфига:
```sh
server {
        listen 443 ssl;
        server_name meta2.mos.ru;

        ssl_certificate /etc/ssl/localhost.crt;
        ssl_certificate_key /etc/ssl/localhost.key;

        location / {
            proxy_pass http://localhost:3000;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }

        location /auth/user {
            proxy_pass https://smart-stage.mos.ru/auth/user;
            proxy_set_header Referer "";
            add_header 'Access-Control-Allow-Origin' '*';
            proxy_set_header Cookie $http_cookie;
        }
}
```
В конфиге нужно указать пути к сгенерированным сертификату и ключу ssl_certificate и ssl_certificate_key
[Как сгенерировать ключи](https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-nginx-in-ubuntu-16-04)

### Порядок действий:
- Запустить VPN
- Перейти на meta2.mos.ru (должен произойти редирект на авторизацию)
- Авторизоваться, подтвердить 2FA. На этом этапе для домена meta2.mos.ru должны быть получены куки, которые нужны будут для работы с профилем (kc-access, OAuth_Token_Request_State, request_uri)
- VPN нужно выключить и теперь нужно запустить фронт локально
```
node server.js
```
- Прописать в hosts (/etc/hosts для Linux или c:/Windows/System32/drivers/etc/hosts для Windows) сопоставление meta2.mos.ru с 127.0.0.1 (При следующей авторизации придётся комментировать эту строку)
```
...
127.0.0.1   meta2.mos.ru
...
```
- Теперь, при попытке перейти на meta2.mos.ru nginx проксирует наш запрос на локальный фронт в дев-режиме. Убедиться в этом можно, пройдя по адресу https://meta2.mos.ru/auth/user - должны получить информацию о пользователе.