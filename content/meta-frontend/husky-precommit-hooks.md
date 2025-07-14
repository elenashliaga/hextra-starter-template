---
title: Husky
type: docs
weight: 6
---

## Husky precommit hooks
Для unit систем hooks могут не запускать из-за прав(выводило ошибка: hint: The '.husky/pre-commit' hook was ignored because it's not set as executable.), решение:
chmod ug+x .husky/*
chmod ug+x .git/hooks/*

## Ссылки
- [Руководство по установке и настройке Meta Frontend](../README.md)
