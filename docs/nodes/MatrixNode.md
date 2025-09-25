# MatrixNode (`MatrixNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Chat |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Matrix, Chat |

**Описание:** Узел для работы с Matrix API.

## Параметры конструктора

- **server_url**: `string` (обяз.). 
- **access_token**: `string` (обяз.). 
- **method**: `string (enum: get_event, send_message, get_messages, get_members, whoami, create_room, join_room, leave_room, invite_user, kick_user, upload_media, sync)`. 
- **timeout**: `integer`. . По умолчанию: `10`
## Входы

### Входы метода `get_event`

- **params**: `object` (обяз.). Параметры запроса.
  - **room_id**: `string` (обяз.). 
  - **event_id**: `string` (обяз.). 

### Входы метода `send_message`

- **params**: `object` (обяз.). Параметры запроса.
  - **room_id**: `string` (обяз.). 
  - **message**: `string` (обяз.). 
  - **msgtype**: `string` (обяз.). 

### Входы метода `get_messages`

- **params**: `object` (обяз.). Параметры запроса.
  - **room_id**: `string` (обяз.). 
  - **limit**: `integer` (обяз.). 
  - **from_token**: `Union[string, null]` (обяз.). 

### Входы метода `get_members`

- **params**: `object` (обяз.). Параметры запроса.
  - **room_id**: `string` (обяз.). 

### Входы метода `whoami`

- **params**: `object` (обяз.). Параметры запроса.

### Входы метода `create_room`

- **params**: `object` (обяз.). Параметры запроса.
  - **name**: `string` (обяз.). 
  - **preset**: `string` (обяз.). 
  - **room_alias**: `Union[string, null]` (обяз.). 

### Входы метода `join_room`

- **params**: `object` (обяз.). Параметры запроса.
  - **room_id_or_alias**: `string` (обяз.). 

### Входы метода `leave_room`

- **params**: `object` (обяз.). Параметры запроса.
  - **room_id**: `string` (обяз.). 

### Входы метода `invite_user`

- **params**: `object` (обяз.). Параметры запроса.
  - **room_id**: `string` (обяз.). 
  - **user_id**: `string` (обяз.). 

### Входы метода `kick_user`

- **params**: `object` (обяз.). Параметры запроса.
  - **room_id**: `string` (обяз.). 
  - **user_id**: `string` (обяз.). 
  - **reason**: `Union[string, null]` (обяз.). 

### Входы метода `upload_media`

- **params**: `object` (обяз.). Параметры запроса.
  - **file_path**: `string` (обяз.). 
  - **room_id**: `string` (обяз.). 
  - **msgtype**: `string` (обяз.). 
  - **message**: `Union[string, null]` (обяз.). 

### Входы метода `sync`

- **params**: `object` (обяз.). Параметры запроса.
  - **room_id**: `string` (обяз.). 
  - **timeout**: `integer` (обяз.). 
  - **since**: `Union[string, null]` (обяз.). 

## Выходы

### Выходы метода `get_event`

- **result**: `string`. 

### Выходы метода `send_message`

- **result**: `string`. 

### Выходы метода `get_messages`

- **result**: `string`. 

### Выходы метода `get_members`

- **result**: `string`. 

### Выходы метода `whoami`

- **result**: `string`. 

### Выходы метода `create_room`

- **result**: `string`. 

### Выходы метода `join_room`

- **result**: `string`. 

### Выходы метода `leave_room`

- **result**: `string`. 

### Выходы метода `invite_user`

- **result**: `string`. 

### Выходы метода `kick_user`

- **result**: `string`. 

### Выходы метода `upload_media`

- **result**: `string`. 

### Выходы метода `sync`

- **result**: `string`. 

## Примеры вызова через ранер

### Пример 1: Получить событие по ID.

**Конфигурация ноды:**
```json
{
  "uuid": "matrixnode_get_event_example",
  "name": "MatrixNode - get_event",
  "type": "MatrixNode",
  "parameters": {
    "server_url": "example_value",
    "access_token": "example_value"
  },
  "inputs": {
    "params": {
      "room_id": "example_value",
      "event_id": "example_value"
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

### Пример 2: Отправить сообщение в чат.

**Конфигурация ноды:**
```json
{
  "uuid": "matrixnode_send_message_example",
  "name": "MatrixNode - send_message",
  "type": "MatrixNode",
  "parameters": {
    "server_url": "example_value",
    "access_token": "example_value"
  },
  "inputs": {
    "params": {
      "room_id": "example_value",
      "message": "example_value",
      "msgtype": "m.text"
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

### Пример 3: Получить несколько сообщений из комнаты.

**Конфигурация ноды:**
```json
{
  "uuid": "matrixnode_get_messages_example",
  "name": "MatrixNode - get_messages",
  "type": "MatrixNode",
  "parameters": {
    "server_url": "example_value",
    "access_token": "example_value"
  },
  "inputs": {
    "params": {
      "room_id": "example_value",
      "limit": 10
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
**Путь:** `matrix\MatrixNode.yaml`
