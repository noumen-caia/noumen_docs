# WaitNode (`WaitNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Control |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | ControlFlow, Temporal |

**Описание:** Нода ожидания: таймер, дата/время или внешний сигнал

## Параметры конструктора

- **method**: `string (enum: timer, datetime, webhook)` (обяз.). 
## Входы

### Входы метода `timer`

- **seconds**: `integer` (обяз.). Количество секунд для ожидания.

### Входы метода `datetime`

- **datetime**: `string` (обяз.). Дата/время в будущем в формате ISO 8601.

### Входы метода `webhook`

- **result**: `object`. Ожидание внешнего сигнала (webhook).
  - _Структура объекта не детализирована в схеме._

## Выходы

### Выходы метода `timer`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `datetime`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `webhook`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

## Примеры вызова через ранер

### Пример 1: Таймер ожидания.

**Конфигурация ноды:**
```json
{
  "uuid": "waitnode_timer_example",
  "name": "WaitNode - timer",
  "type": "WaitNode",
  "parameters": {
    "method": "timer"
  },
  "inputs": {
    "seconds": 1
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

### Пример 2: Ожидание до указанной даты/времени (ISO 8601).

**Конфигурация ноды:**
```json
{
  "uuid": "waitnode_datetime_example",
  "name": "WaitNode - datetime",
  "type": "WaitNode",
  "parameters": {
    "method": "timer"
  },
  "inputs": {
    "datetime": "example_value"
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

### Пример 3: Ожидание внешнего сигнала (webhook).

**Конфигурация ноды:**
```json
{
  "uuid": "waitnode_webhook_example",
  "name": "WaitNode - webhook",
  "type": "WaitNode",
  "parameters": {
    "method": "timer"
  },
  "inputs": {},
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
**Путь:** `wait_node\WaitNode.yaml`
