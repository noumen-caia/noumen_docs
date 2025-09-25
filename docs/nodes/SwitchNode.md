# SwitchNode (`SwitchNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Logic |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Logic, Switch |

**Описание:** Нода для ветвления по правилам

## Параметры конструктора

- **method**: `string (enum: evaluate_rules)`. 
- **timeout**: `integer`. . По умолчанию: `10`
## Входы

### Входы метода `evaluate_rules`

- **rules**: `array[object]` (обяз.). Список правил для ветвления
  - **Структура элементов массива:**
    - **operator**: `object` (обяз.). 
      - **type**: `string (enum: string, number, bool)` (обяз.). Тип данных для сравнения
      - **operation**: `string (enum: equals, not_equals, contains, not_contains, greater_than, less_than)` (обяз.). Операция сравнения
    - **leftValue**: `string` (обяз.). Левое значение (может быть шаблоном)
    - **rightValue**: `unknown` (обяз.). Правое значение
    - **case**: `string` (обяз.). Название ветки для данного правила
- **items**: `array[object]`. Список элементов для обработки

## Выходы

### Выходы метода `evaluate_rules`

- **case**: `unknown`. Активные ветки (строка или список строк)

## Примеры вызова через ранер

### Пример 1: Переключение между ветками на основе значения

**Конфигурация ноды:**
```json
{
  "uuid": "switch_node_example",
  "name": "SwitchNode Example",
  "type": "SwitchNode",
  "parameters": {
    "method": "switch"
  },
  "inputs": {
    "value": "{{previous_node.category}}",
    "cases": {
      "news": "news_processor",
      "data": "data_processor",
      "default": "default_processor"
    }
  },
  "next": [
    "news_processor",
    "data_processor",
    "default_processor"
  ]
}
```

**Ожидаемый результат:**
```json
{
  "matched_case": "news",
  "next_node": "news_processor"
}
```

## Информация о файле
**Путь:** `switch_node\SwitchNode.yaml`
