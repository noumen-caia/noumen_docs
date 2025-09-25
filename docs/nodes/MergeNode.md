# MergeNode (`MergeNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data |

**Описание:** Узел для объединения данных из различных источников

## Параметры конструктора

- **method**: `string (enum: append, combine_by_matching_fields, combine_by_position, combine_by_all_possible_combinations, combine_by_sql_query, choose_branch)` (обяз.). 
## Входы

### Входы метода `append`

- **inputs**: `array[array]` (обяз.). Список входных данных

### Входы метода `combine_by_matching_fields`

- **inputs**: `array[array]` (обяз.). Список входных данных
- **fields_to_match**: `array[string]` (обяз.). Список полей для сопоставления
- **output_type**: `string`. Тип вывода. Возможные значения:
- "keep_matches" - сохранять только сопоставленные элементы (внутреннее соединение)
- "keep_non_matches" - сохранять только несопоставленные элементы
- "keep_everything" - сохранять все элементы (внешнее соединение)
- "enrich_input1" - сохранять все элементы из первого входа и добавлять сопоставленные из остальных
- **clash_handling**: `string`. Обработка конфликтов полей. Возможные значения:
- "input1" - приоритет первого входа
- "input2" - приоритет второго входа
- "last_input" - приоритет последнего входа
- "append_input_number" - добавлять номер входа к имени поля
- **fuzzy_compare**: `boolean`. Сравнивать ли значения с учетом типа
- **multiple_matches**: `string`. Обработка множественных совпадений. Возможные значения:
- "include_all_matches" - включать все совпадения
- "include_first_match_only" - включать только первое совпадение
- **deep_merge**: `boolean`. Объединять ли вложенные поля

### Входы метода `combine_by_position`

- **inputs**: `array[array]` (обяз.). Список входных данных
- **include_unpaired**: `boolean`. Включать ли несопоставленные элементы

### Входы метода `combine_by_all_possible_combinations`

- **inputs**: `array[array]` (обяз.). Список входных данных
- **clash_handling**: `string`. Обработка конфликтов полей
- **deep_merge**: `boolean`. Объединять ли вложенные поля

### Входы метода `combine_by_sql_query`

- **inputs**: `array[array]` (обяз.). Список входных данных
- **sql_query**: `string` (обяз.). SQL-запрос для объединения

### Входы метода `choose_branch`

- **inputs**: `array[array]` (обяз.). Список входных данных
- **branch_to_choose**: `string` (обяз.). Вход для выбора ("input1", "input2", ..., "inputN" или "empty")

## Выходы

### Выходы метода `append`

- **items**: `array[object]`. 
  - _Структура элементов объекта не детализирована в схеме._

### Выходы метода `combine_by_matching_fields`

- **items**: `array[object]`. 
  - _Структура элементов объекта не детализирована в схеме._

### Выходы метода `combine_by_position`

- **items**: `array[object]`. 
  - _Структура элементов объекта не детализирована в схеме._

### Выходы метода `combine_by_all_possible_combinations`

- **items**: `array[object]`. 
  - _Структура элементов объекта не детализирована в схеме._

### Выходы метода `combine_by_sql_query`

- **items**: `array[object]`. 
  - _Структура элементов объекта не детализирована в схеме._

### Выходы метода `choose_branch`

- **items**: `array[object]`. 
  - _Структура элементов объекта не детализирована в схеме._

## Примеры вызова через ранер

### Пример 1: Объединяет данные из всех входов, добавляя их последовательно.

**Конфигурация ноды:**
```json
{
  "uuid": "mergenode_append_example",
  "name": "MergeNode - append",
  "type": "MergeNode",
  "parameters": {
    "method": "append"
  },
  "inputs": {
    "inputs": [
      "item1",
      "item2"
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
  }
]
```

### Пример 2: Объединяет данные из входов, сопоставляя их по указанным полям.

**Конфигурация ноды:**
```json
{
  "uuid": "mergenode_combine_by_matching_fields_example",
  "name": "MergeNode - combine_by_matching_fields",
  "type": "MergeNode",
  "parameters": {
    "method": "append"
  },
  "inputs": {
    "inputs": [
      "item1",
      "item2"
    ],
    "fields_to_match": [
      "item1",
      "item2"
    ],
    "output_type": "keep_matches",
    "clash_handling": "input2",
    "fuzzy_compare": false,
    "multiple_matches": "include_all_matches",
    "deep_merge": false
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
  }
]
```

### Пример 3: Объединяет данные из входов, сопоставляя их по позиции.

**Конфигурация ноды:**
```json
{
  "uuid": "mergenode_combine_by_position_example",
  "name": "MergeNode - combine_by_position",
  "type": "MergeNode",
  "parameters": {
    "method": "append"
  },
  "inputs": {
    "inputs": [
      "item1",
      "item2"
    ],
    "include_unpaired": false
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
  }
]
```

## Информация о файле
**Путь:** `merge\MergeNode.yaml`
