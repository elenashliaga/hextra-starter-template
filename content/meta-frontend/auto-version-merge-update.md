---
title: Авто обновление версии после MR merge
type: docs
weight: 3
---

## Авто обновление версии после MR merge

### При создании Merge request нужно сделать следующее:
1. Выполнить команду node ./scripts/generate-version-up-json.js "new_version_descript_text_here" type_here
```
new_version_descript_text_here - любой текст описания новой версии
type_here -может быть major или minor или patch
```
2. При подмерживании в себе в ветку ветки develop просто выполняет команду еще раз c предидущими значениями
```
node ./scripts/generate-version-up-json.js "new_version_descript_text_here" type_here
```
3. Очень важно при мерже коммита дожадаться завершения gitlab pipeline version перед нажатие кнопки merge на следующем коммите(обычно это занимает примерно 10 сек)
