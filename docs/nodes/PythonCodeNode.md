# PythonCodeNode (`PythonCodeNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Code |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Code, Python |

**Описание:** Нода для выполнения произвольного Python-кода в изолированной среде (ArgoCD)

## Параметры конструктора

- **dockerfile**: `string`. 
- **files**: `object`. 
- **timeout**: `integer`. 
## Входы

- **code**: `string` (обяз.). Python-код для выполнения
- **inputs**: `string`. Входные данные для кода
## Выходы

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._
## Примеры вызова через ранер

### Пример 1: Выполнение PythonCodeNode

**Конфигурация ноды:**
```json
{
  "uuid": "pythoncodenode_example",
  "name": "PythonCodeNode Example",
  "type": "PythonCodeNode",
  "parameters": {},
  "inputs": {
    "code": "example_value",
    "inputs": "example_value"
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
**Путь:** `python_code\PythonCodeNode.yaml`
