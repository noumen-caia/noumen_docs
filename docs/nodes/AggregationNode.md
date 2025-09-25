# AggregationNode (`AggregationNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data, PG |

**Описание:** Узел для агрегации данных

## Параметры конструктора

- **method**: `string (enum: aggregate_by_list, aggregate_by_sum, aggregate_by_avg, aggregate_by_min, aggregate_by_max, aggregate_by_count, aggregate_by_join, aggregate_by_set)` (обяз.). 
## Входы

### Входы метода `aggregate_by_list`

- **items**: `string` (обяз.). Список словарей 
- **field_name**: `string`. Имя ключа в исходном списке. Defaults to 'result'
- **output_field_name**: `string`. Имя ключа в результате выполнения метода. Defaults to 'result'
- **transform**: `string`. Трансформация данных в виде строки. Defaults to None
- **filter**: `string`. Фильтр данных в виде строки. Defaults to None

### Входы метода `aggregate_by_sum`

- **items**: `string` (обяз.). Список словарей 
- **field_name**: `string`. Имя ключа в исходном списке. Defaults to 'result'
- **output_field_name**: `string`. Имя ключа в результате выполнения метода. Defaults to 'result'
- **transform**: `string`. Трансформация данных в виде строки. Defaults to None
- **filter**: `string`. Фильтр данных в виде строки. Defaults to None

### Входы метода `aggregate_by_avg`

- **items**: `string` (обяз.). Список словарей 
- **field_name**: `string`. Имя ключа в исходном списке. Defaults to 'result'
- **output_field_name**: `string`. Имя ключа в результате выполнения метода. Defaults to 'result'
- **transform**: `string`. Трансформация данных в виде строки. Defaults to None
- **filter**: `string`. Фильтр данных в виде строки. Defaults to None

### Входы метода `aggregate_by_min`

- **items**: `string` (обяз.). Список словарей 
- **field_name**: `string`. Имя ключа в исходном списке. Defaults to 'result'
- **output_field_name**: `string`. Имя ключа в результате выполнения метода. Defaults to 'result'
- **transform**: `string`. Трансформация данных в виде строки. Defaults to None
- **filter**: `string`. Фильтр данных в виде строки. Defaults to None

### Входы метода `aggregate_by_max`

- **items**: `string` (обяз.). Список словарей 
- **field_name**: `string`. Имя ключа в исходном списке. Defaults to 'result'
- **output_field_name**: `string`. Имя ключа в результате выполнения метода. Defaults to 'result'
- **transform**: `string`. Трансформация данных в виде строки. Defaults to None
- **filter**: `string`. Фильтр данных в виде строки. Defaults to None

### Входы метода `aggregate_by_count`

- **items**: `string` (обяз.). Список словарей 
- **field_name**: `string`. Имя ключа в исходном списке. Defaults to 'result'
- **output_field_name**: `string`. Имя ключа в результате выполнения метода. Defaults to 'result'
- **transform**: `string`. Трансформация данных в виде строки. Defaults to None
- **filter**: `string`. Фильтр данных в виде строки. Defaults to None

### Входы метода `aggregate_by_join`

- **items**: `string` (обяз.). Список словарей 
- **field_name**: `string`. Имя ключа в исходном списке. Defaults to 'result'
- **output_field_name**: `string`. Имя ключа в результате выполнения метода. Defaults to 'result'
- **transform**: `string`. Трансформация данных в виде строки. Defaults to None
- **filter**: `string`. Фильтр данных в виде строки. Defaults to None
- **separator**: `string`. Разделитель. Defaults to ' '

### Входы метода `aggregate_by_set`

- **items**: `string` (обяз.). Список словарей 
- **field_name**: `string`. Имя ключа в исходном списке. Defaults to 'result'
- **output_field_name**: `string`. Имя ключа в результате выполнения метода. Defaults to 'result'
- **transform**: `string`. Трансформация данных в виде строки. Defaults to None
- **filter**: `string`. Фильтр данных в виде строки. Defaults to None

## Выходы

### Выходы метода `aggregate_by_list`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `aggregate_by_sum`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `aggregate_by_avg`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `aggregate_by_min`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `aggregate_by_max`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `aggregate_by_count`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `aggregate_by_join`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `aggregate_by_set`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

## Примеры вызова через ранер

### Пример 1: Возвращает список элементов по выбранному ключу

**Конфигурация ноды:**
```json
{
  "uuid": "aggregationnode_aggregate_by_list_example",
  "name": "AggregationNode - aggregate_by_list",
  "type": "AggregationNode",
  "parameters": {
    "method": "aggregate_by_list"
  },
  "inputs": {
    "items": "example_value",
    "field_name": "result",
    "output_field_name": "result",
    "transform": "example_value",
    "filter": "example_value"
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

### Пример 2: Возвращает сумму элементов

**Конфигурация ноды:**
```json
{
  "uuid": "aggregationnode_aggregate_by_sum_example",
  "name": "AggregationNode - aggregate_by_sum",
  "type": "AggregationNode",
  "parameters": {
    "method": "aggregate_by_list"
  },
  "inputs": {
    "items": "example_value",
    "field_name": "result",
    "output_field_name": "result",
    "transform": "example_value",
    "filter": "example_value"
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

### Пример 3: Возвращает среднее значение элементов

**Конфигурация ноды:**
```json
{
  "uuid": "aggregationnode_aggregate_by_avg_example",
  "name": "AggregationNode - aggregate_by_avg",
  "type": "AggregationNode",
  "parameters": {
    "method": "aggregate_by_list"
  },
  "inputs": {
    "items": "example_value",
    "field_name": "result",
    "output_field_name": "result",
    "transform": "example_value",
    "filter": "example_value"
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
**Путь:** `aggregation\AggregationNode.yaml`
