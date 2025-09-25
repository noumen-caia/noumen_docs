# IfNode (`IfNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Logic |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Logic, If |

**Описание:** Нода для проверки условий (if)

## Параметры конструктора

- **method**: `string (enum: check_conditions)`. 
- **timeout**: `integer`. . По умолчанию: `10`
## Входы

### Входы метода `check_conditions`

- **conditions**: `object` (обяз.). 
  - **combinator**: `string (enum: and, or)`. Логический оператор для объединения условий
  - **conditions**: `array[object]` (обяз.). Список условий
    - **Структура элементов массива:**
      - **operator**: `object`. 
        - **type**: `string (enum: string, number, bool)` (обяз.). Тип данных для сравнения
        - **operation**: `string (enum: equals, not_equals, contains, not_contains, greater_than, less_than)` (обяз.). Операция сравнения
      - **leftValue**: `string`. Левое значение (может быть шаблоном)
      - **rightValue**: `unknown`. Правое значение
- **options**: `object` (обяз.). 
  - **ignore_case**: `boolean`. Игнорировать регистр при сравнении строк

## Выходы

### Выходы метода `check_conditions`

- **condition**: `boolean`. Результат проверки условий

## Примеры вызова через ранер

### Пример 1: Условное выполнение веток workflow

**Конфигурация ноды:**
```json
{
  "uuid": "if_node_example",
  "name": "IfNode Example",
  "type": "IfNode",
  "parameters": {
    "method": "if"
  },
  "inputs": {
    "condition": "{{previous_node.status}} == 'success'",
    "true_branch": "success_node",
    "false_branch": "error_node"
  },
  "next": [
    "success_node",
    "error_node"
  ]
}
```

**Ожидаемый результат:**
```json
{
  "branch": "success",
  "condition_result": true
}
```

## Информация о файле
**Путь:** `if_node\IfNode.yaml`
