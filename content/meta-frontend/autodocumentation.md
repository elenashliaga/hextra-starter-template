---
title: Авто обновление версии после MR merge
type: docs
weight: 4
---

## Авто-генерация документации и функциональные точки

- Build проекта документации в папке [ui-docs](frontend%2Fui-docs) и запуск его http://127.0.0.1:8080

```bash
npm run compodoc:build-and-serve
```

- Build проекта документации в папке [ui-docs](frontend%2Fui-docs) и создание архива в [ui-docs.zip](frontend%2Fui-docs.zip)

```bash
npm run compodoc:build:zip
```

- После получения zip архива, его нужно отправить на сервер по ssh папку var/www/ui-docs

```
  scp ui-docs.zip user@ip:../../var/www
```

- Разархивировать в папку и удалить архив

```
  sudo unzip ui-docs.zip
  sudo rm ui-docs.zip
```

- Рестартонуть static server caddy

```
  systemctl reload caddy
```

- Build проекта документации в папке [ui-docs](frontend%2Fui-docs) и создание json в [documentation.json](frontend%2Fdocumentation.json) для возможности посмотреть все сущности документации и формате json(сформировано на основе jsdoc коментариев в коде)

```bash
npm run compodoc:build:json
```

## Ссылки
- [Руководство по установке и настройке Meta Frontend](../README.md)
