# JSONDataNode (`JSONDataNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data |

**Описание:** Узел, возвращающий входные данные без изменений. Используется для тестирования или прямой передачи данных дальше по цепочке.

## Параметры конструктора

- _Параметры не требуются._
## Входы

- **task**: `object` (обяз.). Входной словарь с данными (ожидается JSON-подобный объект)
## Выходы

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._
## Примеры вызова через ранер

### Пример 1: Выполнение JSONDataNode

**Конфигурация ноды:**
```json
{
  "uuid": "jsondatanode_example",
  "name": "JSONDataNode Example",
  "type": "JSONDataNode",
  "parameters": {},
  "inputs": {
    "task": {
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
**Путь:** `jsondata\JSONDataNode.yaml`
