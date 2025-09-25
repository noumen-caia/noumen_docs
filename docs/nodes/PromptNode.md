# PromptNode (`PromptNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Agent |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | LLM, Agent |

**Описание:** Узел для работы с проптами

## Параметры конструктора

- **use_current_layer**: `boolean`. . По умолчанию: `False`
## Входы

- **messages**: `array[object]` (обяз.). 
  - **Структура элементов массива:**
    - **role**: `string` (обяз.). 
    - **content**: `string` (обяз.). 
    - **name**: `string`. 
    - **function_call**: `object`. 
- **insert_messages**: `array[object]`. 
  - **Структура элементов массива:**
    - **role**: `string` (обяз.). 
    - **content**: `string` (обяз.). 
    - **name**: `string`. 
    - **function_call**: `object`. 
- **inputs**: `object`. 
## Выходы

- **messages**: `array[object]`. 
  - **Структура элементов массива:**
    - **role**: `string`. 
    - **content**: `string`. 
    - **name**: `string`. 
    - **function_call**: `object`. 
## Примеры вызова через ранер

### Пример 1: Выполнение PromptNode

**Конфигурация ноды:**
```json
{
  "uuid": "promptnode_example",
  "name": "PromptNode Example",
  "type": "PromptNode",
  "parameters": {},
  "inputs": {
    "messages": [
      {
        "role": "example_value",
        "content": "example_value",
        "name": "example_value",
        "function_call": {
          "key": "value"
        }
      },
      {
        "role": "example_value",
        "content": "example_value",
        "name": "example_value",
        "function_call": {
          "key": "value"
        }
      }
    ],
    "insert_messages": [
      {
        "role": "example_value",
        "content": "example_value",
        "name": "example_value",
        "function_call": {
          "key": "value"
        }
      },
      {
        "role": "example_value",
        "content": "example_value",
        "name": "example_value",
        "function_call": {
          "key": "value"
        }
      }
    ],
    "inputs": {
      "key": "value"
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
**Путь:** `prompt\PromptNode.yaml`
