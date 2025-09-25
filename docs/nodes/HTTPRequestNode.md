# HTTPRequestNode (`HTTPRequestNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data, HTTP |

**Описание:** Узел для работы с HTTP запросами

## Параметры конструктора

- **method**: `string (enum: get, options, trace, head, post, put, patch, delete)` (обяз.). 
## Входы

### Входы метода `get`

- **params**: `object` (обяз.). 
  - **url**: `Union[string, string]` (обяз.). 
  - **headers**: `Union[object, null]`. 
  - **timeout**: `Union[number, null]`. 
  - **auth**: `Union[unknown, null]`. 
  - **cookies**: `Union[object, array[unknown], null]`. 
  - **proxy**: `Union[string, string, null]`. 
  - **follow_redirects**: `boolean`. 
  - **verify**: `boolean`. 
  - **trust_env**: `boolean`. 

### Входы метода `options`

- **params**: `object` (обяз.). 
  - **url**: `Union[string, string]` (обяз.). 
  - **headers**: `Union[object, null]`. 
  - **timeout**: `Union[number, null]`. 
  - **auth**: `Union[unknown, null]`. 
  - **cookies**: `Union[object, array[unknown], null]`. 
  - **proxy**: `Union[string, string, null]`. 
  - **follow_redirects**: `boolean`. 
  - **verify**: `boolean`. 
  - **trust_env**: `boolean`. 

### Входы метода `trace`

- **params**: `object` (обяз.). 
  - **url**: `Union[string, string]` (обяз.). 
  - **headers**: `Union[object, null]`. 
  - **timeout**: `Union[number, null]`. 
  - **auth**: `Union[unknown, null]`. 
  - **cookies**: `Union[object, array[unknown], null]`. 
  - **proxy**: `Union[string, string, null]`. 
  - **follow_redirects**: `boolean`. 
  - **verify**: `boolean`. 
  - **trust_env**: `boolean`. 

### Входы метода `head`

- **params**: `object` (обяз.). 
  - **url**: `Union[string, string]` (обяз.). 
  - **headers**: `Union[object, null]`. 
  - **timeout**: `Union[number, null]`. 
  - **auth**: `Union[unknown, null]`. 
  - **cookies**: `Union[object, array[unknown], null]`. 
  - **proxy**: `Union[string, string, null]`. 
  - **follow_redirects**: `boolean`. 
  - **verify**: `boolean`. 
  - **trust_env**: `boolean`. 

### Входы метода `post`

- **params**: `object` (обяз.). 
  - **url**: `Union[string, string]` (обяз.). 
  - **headers**: `Union[object, null]`. 
  - **timeout**: `Union[number, null]`. 
  - **auth**: `Union[unknown, null]`. 
  - **cookies**: `Union[object, array[unknown], null]`. 
  - **proxy**: `Union[string, string, null]`. 
  - **follow_redirects**: `boolean`. 
  - **verify**: `boolean`. 
  - **trust_env**: `boolean`. 
  - **params**: `Union[object, null]`. 
  - **data**: `Union[object, string, null]`. 
  - **json**: `Union[unknown, null]`. 
  - **files**: `Union[object, null]`. 

### Входы метода `put`

- **params**: `object` (обяз.). 
  - **url**: `Union[string, string]` (обяз.). 
  - **headers**: `Union[object, null]`. 
  - **timeout**: `Union[number, null]`. 
  - **auth**: `Union[unknown, null]`. 
  - **cookies**: `Union[object, array[unknown], null]`. 
  - **proxy**: `Union[string, string, null]`. 
  - **follow_redirects**: `boolean`. 
  - **verify**: `boolean`. 
  - **trust_env**: `boolean`. 
  - **params**: `Union[object, null]`. 
  - **data**: `Union[object, string, null]`. 
  - **json**: `Union[unknown, null]`. 
  - **files**: `Union[object, null]`. 

### Входы метода `patch`

- **params**: `object` (обяз.). 
  - **url**: `Union[string, string]` (обяз.). 
  - **headers**: `Union[object, null]`. 
  - **timeout**: `Union[number, null]`. 
  - **auth**: `Union[unknown, null]`. 
  - **cookies**: `Union[object, array[unknown], null]`. 
  - **proxy**: `Union[string, string, null]`. 
  - **follow_redirects**: `boolean`. 
  - **verify**: `boolean`. 
  - **trust_env**: `boolean`. 
  - **params**: `Union[object, null]`. 
  - **data**: `Union[object, string, null]`. 
  - **json**: `Union[unknown, null]`. 
  - **files**: `Union[object, null]`. 

### Входы метода `delete`

- **params**: `object` (обяз.). 
  - **url**: `Union[string, string]` (обяз.). 
  - **headers**: `Union[object, null]`. 
  - **timeout**: `Union[number, null]`. 
  - **auth**: `Union[unknown, null]`. 
  - **cookies**: `Union[object, array[unknown], null]`. 
  - **proxy**: `Union[string, string, null]`. 
  - **follow_redirects**: `boolean`. 
  - **verify**: `boolean`. 
  - **trust_env**: `boolean`. 

## Выходы

### Выходы метода `get`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `options`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `trace`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `head`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `post`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `put`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `patch`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `delete`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

## Примеры вызова через ранер

### Пример 1: GET запрос

**Конфигурация ноды:**
```json
{
  "uuid": "httprequestnode_get_example",
  "name": "HTTPRequestNode - get",
  "type": "HTTPRequestNode",
  "parameters": {
    "method": "get"
  },
  "inputs": {
    "params": {
      "url": "example_value",
      "timeout": 10.0,
      "follow_redirects": false,
      "verify": true,
      "trust_env": true
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

### Пример 2: OPTIONS запрос

**Конфигурация ноды:**
```json
{
  "uuid": "httprequestnode_options_example",
  "name": "HTTPRequestNode - options",
  "type": "HTTPRequestNode",
  "parameters": {
    "method": "get"
  },
  "inputs": {
    "params": {
      "url": "example_value",
      "timeout": 10.0,
      "follow_redirects": false,
      "verify": true,
      "trust_env": true
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

### Пример 3: TRACE запрос

**Конфигурация ноды:**
```json
{
  "uuid": "httprequestnode_trace_example",
  "name": "HTTPRequestNode - trace",
  "type": "HTTPRequestNode",
  "parameters": {
    "method": "get"
  },
  "inputs": {
    "params": {
      "url": "example_value",
      "timeout": 10.0,
      "follow_redirects": false,
      "verify": true,
      "trust_env": true
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
**Путь:** `http_request\HTTPRequestNode.yaml`
