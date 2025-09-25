# EmailNode (`EmailNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Event |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Email |

**Описание:** Узел для отправки писем

## Параметры конструктора

- **credentials**: `object` (обяз.). Учётные данные
  - **host**: `string` (обяз.). хост
  - **port**: `Union[integer, null]`. порт
  - **sender**: `string` (обяз.). отправитель
  - **password**: `string` (обяз.). пароль
## Входы

- **recipients**: `Union[string, array[string]]` (обяз.). названия набора данных
- **subject**: `string` (обяз.). тема письма
- **text**: `Union[string, array[string]]` (обяз.). текст письма
- **image**: `string`. изображение. Defaults to None.
## Выходы

- **status**: `string (enum: success, no succeess)`. 
## Примеры вызова через ранер

### Пример 1: Выполнение EmailNode

**Конфигурация ноды:**
```json
{
  "uuid": "emailnode_example",
  "name": "EmailNode Example",
  "type": "EmailNode",
  "parameters": {
    "credentials": {
      "host": "https://example.com",
      "port": 8080,
      "sender": "example_value",
      "password": "{{env.API_KEY}}"
    }
  },
  "inputs": {
    "recipients": "example_value",
    "subject": "example_value",
    "text": "example_value",
    "image": "example_value"
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
**Путь:** `email_sender\EmailNode.yaml`
