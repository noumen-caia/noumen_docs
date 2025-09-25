# ForEachNode (`ForEachNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | WorkFlow |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | WorkFlow |

**Описание:** Узел для запуска подпроцесса для каждого экзепляра входных данных

## Параметры конструктора

- **batch_size**: `integer`. Количество элементов, которые передаются в подпроцесс. По умолчанию: `1`
- **async**: `boolean`. Запускать подпроцессы параллельно. По умолчанию: `False`
## Входы

- **items**: `array`. Список из элементов
## Выходы

- **result**: `array`. 
## Примеры вызова через ранер

### Пример 1: Итерация по списку элементов с выполнением под-workflow

**Конфигурация ноды:**
```json
{
  "uuid": "foreach_node_example",
  "name": "ForEachNode Example",
  "type": "ForEachNode",
  "parameters": {
    "async": false
  },
  "inputs": {
    "items": "{{previous_node.results}}"
  },
  "nodes": [
    {
      "uuid": "process_item",
      "name": "ProcessItem",
      "type": "JSONDataNode",
      "parameters": {},
      "inputs": {
        "task": {
          "item": "{{foreach.context}}",
          "processed": true
        }
      }
    }
  ],
  "next": [
    "aggregation_node"
  ]
}
```

**Ожидаемый результат:**
```json
[
  {
    "item": {
      "id": 1,
      "name": "item1"
    },
    "processed": true
  },
  {
    "item": {
      "id": 2,
      "name": "item2"
    },
    "processed": true
  }
]
```

## Информация о файле
**Путь:** `foreach\ForEachNode.yaml`
