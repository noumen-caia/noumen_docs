# TablePreviewNode (`TablePreviewNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Preview |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data, Table |

**Описание:** Узел, возвращающий входные данные в виде таблицы.

## Параметры конструктора

- **max_rows**: `integer`. . По умолчанию: `10`
- **title**: `string`. . По умолчанию: `Table Preview`
## Входы

- **items**: `array[object]` (обяз.). Список словарей с данными
## Выходы

- **items**: `array[object]`. 
  - _Структура элементов объекта не детализирована в схеме._
## Примеры вызова через ранер

### Пример 1: Выполнение TablePreviewNode

**Конфигурация ноды:**
```json
{
  "uuid": "tablepreviewnode_example",
  "name": "TablePreviewNode Example",
  "type": "TablePreviewNode",
  "parameters": {},
  "inputs": {
    "items": [
      {
        "id": 1,
        "name": "item1"
      },
      {
        "id": 2,
        "name": "item2"
      }
    ]
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
[
  {
    "id": 1,
    "name": "Item 1",
    "status": "active"
  },
  {
    "id": 2,
    "name": "Item 2",
    "status": "pending"
  },
  {
    "id": 3,
    "name": "Item 3",
    "status": "completed"
  }
]
```

## Информация о файле
**Путь:** `table_preview\TablePreviewNode.yaml`
