# EditFieldNode (`EditFieldNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data |

**Описание:** Узел для редактирования полей

## Параметры конструктора

- **method**: `string (enum: insert_manual, insert_json)` (обяз.). 
## Входы

### Входы метода `insert_manual`

- **fields_to_set**: `array[object]` (обяз.). Ключ и значение
  - **Структура элементов массива:**
    - **field_name**: `string` (обяз.). 
    - **field_value**: `Union[object, string, number, integer, boolean]` (обяз.). 
- **inputs**: `object` (обяз.). Словарь со значениями для подстановки

### Входы метода `insert_json`

- **json_schema**: `object` (обяз.). Словарь для вставки значений
- **inputs**: `object` (обяз.). Словарь со значениями для подстановки в json_schema

## Выходы

### Выходы метода `insert_manual`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `insert_json`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

## Примеры вызова через ранер

### Пример 1: Ручная настройка полей

**Конфигурация ноды:**
```json
{
  "uuid": "editfieldnode_insert_manual_example",
  "name": "EditFieldNode - insert_manual",
  "type": "EditFieldNode",
  "parameters": {
    "method": "insert_manual"
  },
  "inputs": {
    "fields_to_set": [
      {
        "field_name": "example_value",
        "field_value": {
          "key": "value"
        }
      },
      {
        "field_name": "example_value",
        "field_value": {
          "key": "value"
        }
      }
    ],
    "inputs": {
      "key": "value"
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
  "status": "success",
  "data": {
    "processed": 3,
    "failed": 0,
    "results": [
      {
        "id": 1,
        "status": "completed"
      },
      {
        "id": 2,
        "status": "completed"
      }
    ]
  },
  "metadata": {
    "timestamp": "2024-01-15T14:30:00Z",
    "version": "1.0.0"
  }
}
```

### Пример 2: Форматирование переменных в json_schema

**Конфигурация ноды:**
```json
{
  "uuid": "editfieldnode_insert_json_example",
  "name": "EditFieldNode - insert_json",
  "type": "EditFieldNode",
  "parameters": {
    "method": "insert_manual"
  },
  "inputs": {
    "json_schema": {
      "key": "value"
    },
    "inputs": {
      "key": "value"
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
  "status": "success",
  "data": {
    "processed": 3,
    "failed": 0,
    "results": [
      {
        "id": 1,
        "status": "completed"
      },
      {
        "id": 2,
        "status": "completed"
      }
    ]
  },
  "metadata": {
    "timestamp": "2024-01-15T14:30:00Z",
    "version": "1.0.0"
  }
}
```

## Информация о файле
**Путь:** `edit_field\EditFieldNode.yaml`
