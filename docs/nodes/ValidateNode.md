# ValidateNode (`ValidateNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data, Validation |

**Описание:** Узел для валидации данных по JSON Schema с детальной отчетностью об ошибках.

## Параметры конструктора

- **method**: `string (enum: validate_items)`. 
- **timeout**: `integer`. . По умолчанию: `10`
## Входы

### Входы метода `validate_items`

- **params**: `object` (обяз.). Параметры для валидации элементов.
  - **items**: `array[object]` (обяз.). Список элементов для валидации
  - **jsonSchema**: `Union[object, string]` (обяз.). JSON Schema для валидации
  - **fail_on_error**: `boolean` (обяз.). Выбрасывать исключение при первой ошибке

## Выходы

### Выходы метода `validate_items`

- **items**: `array[object]`. Список валидных элементов
- **errors**: `array[unknown]`. Список ошибок валидации

## Примеры вызова через ранер

### Пример 1: Валидация списка элементов по JSON Schema.

**Конфигурация ноды:**
```json
{
  "uuid": "validatenode_validate_items_example",
  "name": "ValidateNode - validate_items",
  "type": "ValidateNode",
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
      "jsonSchema": {
        "key": "value"
      },
      "fail_on_error": true
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
  "errors": [
    "item1",
    "item2"
  ]
}
```

## Информация о файле
**Путь:** `validate\ValidateNode.yaml`
