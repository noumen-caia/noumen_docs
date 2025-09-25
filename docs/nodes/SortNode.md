# SortNode (`SortNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data, Sort |

**Описание:** Узел для сортировки массивов данных с поддержкой различных алгоритмов сортировки.

## Параметры конструктора

- **method**: `string (enum: simple_sort, random_sort, code_sort)`. 
- **timeout**: `integer`. . По умолчанию: `10`
## Входы

### Входы метода `simple_sort`

- **params**: `object` (обяз.). Параметры для простой сортировки.
  - **items**: `array[object]` (обяз.). Список элементов для сортировки
  - **sortFields**: `array[unknown]` (обяз.). Поля для сортировки
  - **options**: `unknown` (обяз.). Опции сортировки

### Входы метода `random_sort`

- **params**: `object` (обяз.). Параметры для случайной сортировки.
  - **items**: `array[object]` (обяз.). Список элементов для сортировки

### Входы метода `code_sort`

- **params**: `object` (обяз.). Параметры для кастомной сортировки.
  - **items**: `array[object]` (обяз.). Список элементов для сортировки
  - **code**: `string` (обяз.). Python код для кастомной сортировки

## Выходы

### Выходы метода `simple_sort`

- **items**: `array[object]`. Отсортированный список элементов

### Выходы метода `random_sort`

- **items**: `array[object]`. Отсортированный список элементов

### Выходы метода `code_sort`

- **items**: `array[object]`. Отсортированный список элементов

## Примеры вызова через ранер

### Пример 1: Выполнить простую сортировку по полям.

**Конфигурация ноды:**
```json
{
  "uuid": "sortnode_simple_sort_example",
  "name": "SortNode - simple_sort",
  "type": "SortNode",
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
      "sortFields": [
        "item1",
        "item2"
      ]
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
  ]
}
```

### Пример 2: Выполнить случайную сортировку элементов.

**Конфигурация ноды:**
```json
{
  "uuid": "sortnode_random_sort_example",
  "name": "SortNode - random_sort",
  "type": "SortNode",
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
      ]
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
  ]
}
```

### Пример 3: Выполнить кастомную сортировку через Python код.

**Конфигурация ноды:**
```json
{
  "uuid": "sortnode_code_sort_example",
  "name": "SortNode - code_sort",
  "type": "SortNode",
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
      "code": "example_value"
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
  ]
}
```

## Информация о файле
**Путь:** `sort\SortNode.yaml`
