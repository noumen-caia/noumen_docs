# DateTimeNode (`DateTimeNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | DateTime |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Date, Time, Datetime |

**Описание:** Нода для работы с датой и временем.

## Параметры конструктора

- **method**: `string (enum: add, subtract, extract, format, now, diff, round)`. 
## Входы

### Входы метода `add`

- **params**: `object` (обяз.). Параметры.
  - **date**: `string` (обяз.). 
  - **years**: `Union[integer, null]`. 
  - **months**: `Union[integer, null]`. 
  - **days**: `Union[integer, null]`. 
  - **hours**: `Union[integer, null]`. 
  - **minutes**: `Union[integer, null]`. 
  - **seconds**: `Union[integer, null]`. 

### Входы метода `subtract`

- **params**: `object` (обяз.). Параметры.
  - **date**: `string` (обяз.). 
  - **years**: `Union[integer, null]`. 
  - **months**: `Union[integer, null]`. 
  - **days**: `Union[integer, null]`. 
  - **hours**: `Union[integer, null]`. 
  - **minutes**: `Union[integer, null]`. 
  - **seconds**: `Union[integer, null]`. 

### Входы метода `extract`

- **params**: `object` (обяз.). Параметры.
  - **date**: `string` (обяз.). 
  - **part**: `string`. 

### Входы метода `format`

- **params**: `object` (обяз.). Параметры.
  - **date**: `string` (обяз.). 
  - **format**: `string`. 

### Входы метода `now`

- **params**: `object` (обяз.). Параметры.
  - **timezone**: `string`. 
  - **with_time**: `boolean`. 

### Входы метода `diff`

- **params**: `object` (обяз.). Параметры.
  - **date1**: `string` (обяз.). 
  - **date2**: `string` (обяз.). 
  - **units**: `Union[string, array[string]]`. 

### Входы метода `round`

- **params**: `object` (обяз.). Параметры.
  - **date**: `string` (обяз.). 
  - **unit**: `string`. 

## Выходы

### Выходы метода `add`

- **result**: `string`. 

### Выходы метода `subtract`

- **result**: `string`. 

### Выходы метода `extract`

- **result**: `string`. 

### Выходы метода `format`

- **result**: `string`. 

### Выходы метода `now`

- **result**: `string`. 

### Выходы метода `diff`

- **result**: `string`. 

### Выходы метода `round`

- **result**: `string`. 

## Примеры вызова через ранер

### Пример 1: Добавить время к дате.

**Конфигурация ноды:**
```json
{
  "uuid": "datetimenode_add_example",
  "name": "DateTimeNode - add",
  "type": "DateTimeNode",
  "parameters": {},
  "inputs": {
    "params": {
      "date": "example_value"
    }
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
"example_result"
```

### Пример 2: Вычесть время из даты.

**Конфигурация ноды:**
```json
{
  "uuid": "datetimenode_subtract_example",
  "name": "DateTimeNode - subtract",
  "type": "DateTimeNode",
  "parameters": {},
  "inputs": {
    "params": {
      "date": "example_value"
    }
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
"example_result"
```

### Пример 3: Извлечь часть даты.

**Конфигурация ноды:**
```json
{
  "uuid": "datetimenode_extract_example",
  "name": "DateTimeNode - extract",
  "type": "DateTimeNode",
  "parameters": {},
  "inputs": {
    "params": {
      "date": "example_value",
      "part": "minute"
    }
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
"example_result"
```

## Информация о файле
**Путь:** `datetime\DateTimeNode.yaml`
