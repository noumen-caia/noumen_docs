# SplitOutNode (`SplitOutNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data |

**Описание:** Узел для разделения одного элемента данных, содержащего список, на несколько элементов

## Параметры конструктора

- _Параметры не требуются._
## Входы

- **inputs**: `Union[array[object], object]` (обяз.). Входные данные (список словарей или одиночный словарь)
- **field_to_split_out**: `string` (обяз.). Поле, содержащее список для разделения
- **include**: `string`. Тип включения других полей. Возможные значения:
- "no_other_fields" - не включать другие поля
- "all_other_fields" - включать все другие поля
- "selected_other_fields" - включать только выбранные поля
- **fields_to_include**: `array[string]`. Дополнительные поля для включения в результат
- **destination_field_name**: `string`. Имя поля в выходных данных
- **disable_dot_notation**: `boolean`. Отключить ли точечную нотацию
- **include_binary**: `boolean`. Включать ли бинарные данные
## Выходы

- **items**: `array[object]`. 
  - _Структура элементов объекта не детализирована в схеме._
## Примеры вызова через ранер

### Пример 1: Выполнение SplitOutNode

**Конфигурация ноды:**
```json
{
  "uuid": "splitoutnode_example",
  "name": "SplitOutNode Example",
  "type": "SplitOutNode",
  "parameters": {},
  "inputs": {
    "inputs": [
      "item1",
      "item2"
    ],
    "field_to_split_out": "example_value",
    "include": "all_other_fields",
    "fields_to_include": [
      "item1",
      "item2"
    ],
    "destination_field_name": "example_value",
    "disable_dot_notation": false,
    "include_binary": true
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
**Путь:** `split_out\SplitOutNode.yaml`
