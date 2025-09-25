# FilterNode (`FilterNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Logic |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Filter, Logic |

**Описание:** Фильтрует элементы по условиям

## Параметры конструктора

- **method**: `string (enum: filter)`. . По умолчанию: `filter`
- **timeout**: `integer`. . По умолчанию: `10`
## Входы

### Входы метода `filter`

- **params**: `object` (обяз.). Параметры фильтрации.
  - **items**: `array[object]` (обяз.). 
  - **conditions**: `object` (обяз.). 

## Выходы

### Выходы метода `filter`

- **passed**: `array[object]`. Элементы, прошедшие фильтр
- **failed**: `array[object]`. Элементы, не прошедшие фильтр

## Примеры вызова через ранер

### Пример 1: Фильтрует элементы по условиям.

**Конфигурация ноды:**
```json
{
  "uuid": "filternode_filter_example",
  "name": "FilterNode - filter",
  "type": "FilterNode",
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
      "conditions": {
        "key": "value"
      }
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
  "passed": [
    {
      "id": 1,
      "name": "item1"
    },
    {
      "id": 2,
      "name": "item2"
    }
  ],
  "failed": [
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
**Путь:** `filter_node\FilterNode.yaml`
