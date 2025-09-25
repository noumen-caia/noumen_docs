# Манифест расширения

Каждому расширению необходим файл манифеста `package.json` в корне структуры каталогов расширений.

## Основные поля

| Поле | Тип | Обязательное | Описание |
|------|-----|-------------|----------|
| `name` | string | Да | Уникальное имя расширения |
| `displayName` | string | Да | Отображаемое имя расширения |
| `description` | string | Да | Описание расширения |
| `version` | string | Да | Версия расширения |
| `publisher` | string | Да | Идентификатор издателя |
| `main` | string | Да | Точка входа расширения |
| `contributes` | object | Нет | Точки вклада расширения |


## Пример

```json
{
  "name": "my-first-extension",
  "displayName": "My First Extension",
  "description": "Пример расширения",
  "version": "1.0.0",
  "publisher": "your-name",
  "main": "./extension.js",
  "contributes": {
    "commands": [
      {
        "command": "my-first-extension.helloWorld",
        "title": "Hello World"
      }
    ]
  }
}
```

## Важные примечания

- Поля `name` и `publisher` вместе формируют уникальный идентификатор расширения
- Поле `main` указывает на основной файл JavaScript расширения
- Поле `contributes` определяет, как расширение расширяет функциональность Constructor