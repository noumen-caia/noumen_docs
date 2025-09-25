# Нотации

Нотации — это расширения, которые определяют правила отображения проектов в редакторе нод. Активируются при создании проекта и выборе нотации.

## Конфигурация

```json
{
  "contributes": {
    "notation": {
      "name": "Название нотации",
      "rules": {
        "allowSelfConnections": false,
        "enableNodeGrouping": true,
        "hasMultipleDataPorts": false,
        "hasMultipleExtPorts": false
      },
      "nodes": {
        "label": "unique-name",
        "name": "Библиотека нод",
        "path": "./nodes"
      }
    }
  }
}
```

## Основные параметры

- **`name`** — название нотации (обязательно)
- **`rules`** — правила поведения:
  - `allowSelfConnections` — разрешить самосоединения нод
  - `enableNodeGrouping` — включить группировку нод
  - `hasMultipleDataPorts` — множественные data порты
  - `hasMultipleExtPorts` — множественные execution порты
- **`nodes`** — библиотека нод для нотации
- **`project.enabledChangeName`** — разрешить изменение названия проекта

## Пример

```json
{
  "contributes": {
    "notation": {
      "name": "React Notation",
      "rules": {
        "allowSelfConnections": false,
        "enableNodeGrouping": true
      },
      "nodes": {
        "name": "React Components",
        "label": "react-components",
        "path": "./nodes"
      }
    }
  }
}
```

## Активация

Нотации активируются при:

1. Создании проекта
2. Выборе нотации при создании проекта
3. Переходе в проект с определенной нотацией