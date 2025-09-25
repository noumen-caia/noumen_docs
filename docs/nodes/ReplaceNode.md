# ReplaceNode (`ReplaceNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Обработка текста |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Текст, Замена текста, Регулярные выражения, Regex |

**Описание:** Нода для замены или очистки текстовых полей с использованием регулярных выражений (Regex).

## Параметры конструктора

- **method**: `string (enum: replace_text)`. 
- **timeout**: `integer`. . По умолчанию: `10`
## Входы

### Входы метода `replace_text`

- **params**: `object` (обяз.). 
  - **items**: `array[object]` (обяз.). Список элементов для обработки
  - **fields**: `array[string]` (обяз.). Список полей, которые нужно изменить
  - **pattern**: `string` (обяз.). Регулярное выражение для поиска
  - **replacement**: `string` (обяз.). Строка для замены найденного выражения
  - **flags**: `string` (обяз.). Флаги регулярного выражения (например, i, m)

## Выходы

### Выходы метода `replace_text`

- **result**: `array[object]`. Измененные данные

## Примеры вызова через ранер

### Пример 1: Заменяет текст в указанных полях с использованием регулярных выражений.
Аргументы:
    params (ReplaceNodeParams): Параметры для замены текста.

Возвращает:
    ReplaceNodeResult: Измененные данные.

**Конфигурация ноды:**
```json
{
  "uuid": "replacenode_replace_text_example",
  "name": "ReplaceNode - replace_text",
  "type": "ReplaceNode",
  "parameters": {},
  "inputs": {
    "params": {
      "items": [
        {
          "id": 1,
          "name": "item1"
        },
        {
          "id": 2,
          "name": "item2"
        }
      ],
      "fields": [
        "item1",
        "item2"
      ],
      "pattern": "example_value",
      "replacement": "example_value",
      "flags": ""
    }
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
{
  "result": [
    {
      "id": 1,
      "name": "item1"
    },
    {
      "id": 2,
      "name": "item2"
    }
  ]
}
```

## Информация о файле
**Путь:** `replace\ReplaceNode.yaml`
