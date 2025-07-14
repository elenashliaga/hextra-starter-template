---
title: Обновление версии
type: docs
weight: 12
---

## Обновление версии

Скрипт для формирования changelog и версионирования проекта.
В приложении ведутся 2 версии: client и release.
Release version - общая версия приложения
Client version - версия фронтенд-части

Аргументы:

- type = "minor" - какую версию повышаем (major, minor, patch)
- description = "" - описание изменений в версии
- target = "release" - опциональный аргумент, какой тип версии повышаем, frontend или release (по умолчанию release)

#### Пример использования с повышением client версии:

```bash
node ./version-up.js minor "Обновление архитектуры" frontend
```

#### Пример использования с повышением release версии

```bash
node ./version-up.js major "Мультиплеер"
```

## Ссылки

- [Руководство по установке и настройке Meta Frontend](../README.md)
