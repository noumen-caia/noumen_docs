# ChartPreviewNode (`ChartPreviewNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Preview |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data, Chart, Visualization |

**Описание:** Узел, возвращающий входные данные в виде графиков.

## Параметры конструктора

- **chart_type**: `string`. . По умолчанию: `Line`
- **title**: `string`. . По умолчанию: `Chart Preview`
- **x_field**: `string`. . По умолчанию: `x`
- **y_field**: `string`. . По умолчанию: `y`
- **series_field**: `string`. 
## Входы

- **items**: `array[object]` (обяз.). Список словарей с данными для графика
## Выходы

- **items**: `array[object]`. 
  - _Структура элементов объекта не детализирована в схеме._
## Примеры вызова через ранер

### Пример 1: Выполнение ChartPreviewNode

**Конфигурация ноды:**
```json
{
  "uuid": "chartpreviewnode_example",
  "name": "ChartPreviewNode Example",
  "type": "ChartPreviewNode",
  "parameters": {},
  "inputs": {
    "items": [
      {
        "id": 1,
        "name": "item1"
      },
      {
        "id": 2,
        "name": "item2"
      }
    ]
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
[
  {
    "id": 1,
    "name": "Item 1",
    "status": "active"
  },
  {
    "id": 2,
    "name": "Item 2",
    "status": "pending"
  },
  {
    "id": 3,
    "name": "Item 3",
    "status": "completed"
  }
]
```

## Информация о файле
**Путь:** `chart_preview\ChartPreviewNode.yaml`
