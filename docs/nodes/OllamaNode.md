# OllamaNode (`OllamaNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | AI |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | LLM, Ollama, Embeddings |

**Описание:** Узел для работы с Ollama API

## Параметры конструктора

- **base_url**: `string`. . По умолчанию: `localhost:11434`
- **method**: `string (enum: check_connection, get_available_models, chat, generate, embed, get_embedding_length)`. 
- **timeout**: `integer`. . По умолчанию: `30`
## Входы

### Входы метода `check_connection`

- **timeout**: `number`. Таймаут запроса, сек.

### Входы метода `get_available_models`

- **timeout**: `number`. Таймаут запроса, сек.

### Входы метода `chat`

- **model**: `string` (обяз.). Название модели.
- **messages**: `array[object]` (обяз.). Список сообщений {"role": "system|user|assistant|tool", "content": str}.
- **format**: `string`. Формат ответа. В настоящее время единственное доступное значение — json, опционально.
- **options**: `array[object]`. Доп.параметры модели (список {name,value} или dict), опционально.
- **keep_alive**: `Union[string, integer]`. Время жизни модели после запроса, опционально.
- **timeout**: `number`. Таймаут запроса, сек.
- **stream**: `boolean`. Потоковый ответ (по умолчанию False).

### Входы метода `generate`

- **model**: `string` (обяз.). Название модели (обязательно).
- **prompt**: `string` (обяз.). Текст запроса (обязательно).
- **system**: `string`. Системный промпт (инструкция), опционально.
- **format**: `string`. Формат ответа. В настоящее время единственное доступное значение — json, опционально.
- **options**: `array[object]`. Доп.параметры модели (список {name,value} или dict), опционально.
- **keep_alive**: `Union[string, integer]`. Время жизни модели после запроса, опционально.
- **timeout**: `number`. Таймаут запроса, сек.
- **stream**: `boolean`. Потоковый ответ (по умолчанию False).

### Входы метода `embed`

- **model**: `string` (обяз.). Название модели эмбеддингов (обязательно).
- **input**: `Union[string, array[string]]` (обяз.). Текст или список текстов для векторизации (обязательно).
- **truncate**: `boolean`. Обрезать вход до контекстного окна (bool), опционально.
- **options**: `array[object]`. Доп.параметры модели (список {name,value} или dict), опционально.
- **keep_alive**: `Union[string, integer]`. Время жизни модели после запроса, опционально.
- **timeout**: `number`. Таймаут запроса, сек.

### Входы метода `get_embedding_length`

- **model**: `string` (обяз.). Название модели для проверки (если None — возьмётся дефолт модели на сервере).
- **timeout**: `number`. Таймаут запроса, сек.

## Выходы

### Выходы метода `check_connection`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

### Выходы метода `get_available_models`

- **result**: `string`. 

### Выходы метода `chat`

- **result**: `string`. 

### Выходы метода `generate`

- **result**: `string`. 

### Выходы метода `embed`

- **result**: `string`. 

### Выходы метода `get_embedding_length`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

## Примеры вызова через ранер

### Пример 1: Проверить доступность Ollama API.

**Конфигурация ноды:**
```json
{
  "uuid": "ollamanode_check_connection_example",
  "name": "OllamaNode - check_connection",
  "type": "OllamaNode",
  "parameters": {},
  "inputs": {
    "timeout": 1.0
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

### Пример 2: Получить список доступных моделей.

**Конфигурация ноды:**
```json
{
  "uuid": "ollamanode_get_available_models_example",
  "name": "OllamaNode - get_available_models",
  "type": "OllamaNode",
  "parameters": {},
  "inputs": {
    "timeout": 1.0
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

### Пример 3: Чат с моделью.

**Конфигурация ноды:**
```json
{
  "uuid": "ollamanode_chat_example",
  "name": "OllamaNode - chat",
  "type": "OllamaNode",
  "parameters": {},
  "inputs": {
    "model": "example_value",
    "messages": [
      {
        "id": 1,
        "name": "item1"
      },
      {
        "id": 2,
        "name": "item2"
      }
    ],
    "format": "example_value",
    "options": [
      {
        "id": 1,
        "name": "item1"
      },
      {
        "id": 2,
        "name": "item2"
      }
    ],
    "keep_alive": "example_value",
    "timeout": 1.0,
    "stream": false
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
**Путь:** `ollama\OllamaNode.yaml`
