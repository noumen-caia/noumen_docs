# ConcatenateNode (`ConcatenateNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data |

**Описание:** Узел для row-wise конкатенации полей (склейка значений в новое поле)

## Параметры конструктора

- **method**: `string (enum: concatenate_rowwise)`. 
- **timeout**: `integer`. . По умолчанию: `10`
## Входы

### Входы метода `concatenate_rowwise`

- **params**: `object` (обяз.). 
  - **items**: `array[object]` (обяз.). Входные элементы
  - **fieldsToConcatenate**: `array[string]` (обяз.). Список полей для объединения
  - **outputField**: `string` (обяз.). Имя нового поля для результата
  - **separator**: `string` (обяз.). Разделитель между значениями

## Выходы

### Выходы метода `concatenate_rowwise`

- **result**: `array[object]`. Список элементов с добавленным полем

## Примеры вызова через ранер

### Пример 1: None

**Конфигурация ноды:**
```json
{
  "uuid": "concatenatenode_concatenate_rowwise_example",
  "name": "ConcatenateNode - concatenate_rowwise",
  "type": "ConcatenateNode",
  "parameters": {},
  "inputs": {
    "params": {
      "items": [
        {
          "id": 1,
          "name": "item1"
        },
        {
          "id": 2,
          "name": "item2"
        }
      ],
      "fieldsToConcatenate": [
        "item1",
        "item2"
      ],
      "outputField": "example_value",
      "separator": " "
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
  "result": [
    {
      "id": 1,
      "name": "item1"
    },
    {
      "id": 2,
      "name": "item2"
    }
  ]
}
```

## Информация о файле
**Путь:** `concatenate\ConcatenateNode.yaml`
