# SleepNode (`SleepNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data |

**Описание:** Узел для засыпания на период времени

## Параметры конструктора

- _Параметры не требуются._
## Входы

- **amount**: `integer` (обяз.). Количество времени для ожидания.
- **unit**: `string`. Единица измерения времени. 
Допустимые значения: 'seconds', 'minutes', 'hours'. 
По умолчанию 'seconds'.
## Выходы

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._
## Примеры вызова через ранер

### Пример 1: Выполнение SleepNode

**Конфигурация ноды:**
```json
{
  "uuid": "sleepnode_example",
  "name": "SleepNode Example",
  "type": "SleepNode",
  "parameters": {},
  "inputs": {
    "amount": 1,
    "unit": "seconds"
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
**Путь:** `sleep\SleepNode.yaml`
