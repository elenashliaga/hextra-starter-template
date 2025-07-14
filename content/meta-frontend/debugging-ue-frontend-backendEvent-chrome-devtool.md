---
title: Debug
type: docs
weight: 5
---

# Для отправки события
- открыть сайт c нашим фронтендом http://localhost:4200 или любой другой например https://stage2.sel.metapolis.su/
- щелкнуть правой кнопкой по web иконке - например настройки - для перехвата фокуса и нажать клавишу F12
- Для отправки backendEvent в chrome devtools console выполнить команду
```bash
document.body.dispatchEvent(new CustomEvent('backendEvent', { detail: { method: 'translateCameraToBuilding', params: { buildingId: '5C26AC914E739F46B9851A87E5F2281B' } } }));
```
method  - это название метода для Бэкенд таблицы https://wiki.yandex.ru/homepage/proekty/cifrovojj-dvojjnik-meta-ue5/opornye-stranicy/texnicheskaja-dokumentacija/protokol-json-rpc-2.0-nad-pixel-streaming/metody-i-tipy/?utm_referrer=about%3Ablank
params - это объект в той же Бэкенд таблице

- Для установки подписки на фронтенд событие(frontendEvent) в chrome devtools console выполнить команду
```bash
document.body.dispatchEvent(new CustomEvent('frontendEvent', { detail: { method: 'updateLightActivationType' } }));
```
method  - это название метода для Фронтенд таблицы https://wiki.yandex.ru/homepage/proekty/cifrovojj-dvojjnik-meta-ue5/opornye-stranicy/texnicheskaja-dokumentacija/protokol-json-rpc-2.0-nad-pixel-streaming/metody-i-tipy/?utm_referrer=about%3Ablank


### Видео инструкция:
https://disk.yandex.ru/d/Cqpc2aAHEWfuNw
