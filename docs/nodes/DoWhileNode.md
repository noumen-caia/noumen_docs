# DoWhileNode (`DoWhileNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | WorkFlow |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | WorkFlow |

**Описание:** Узел для запуска подпроцесса хотя бы 1 раз до выполнения уловия остановки

## Параметры конструктора

- **max_iterations**: `integer`. Максимальное количество итераций
- **break_condition**: `string`. Условия остановки
## Входы

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._
## Выходы

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._
## Примеры вызова через ранер

### Пример 1: Циклическое выполнение с условием выхода

**Конфигурация ноды:**
```json
{
  "uuid": "dowhile_node_example",
  "name": "DoWhileNode Example",
  "type": "DoWhileNode",
  "parameters": {
    "break_condition": "'{{while.counter}}' >= '5'",
    "max_iterations": 10
  },
  "inputs": {
    "context": "{{initial_data}}"
  },
  "nodes": [
    {
      "uuid": "increment_counter",
      "name": "IncrementCounter",
      "type": "JSONDataNode",
      "parameters": {},
      "inputs": {
        "task": {
          "counter": "{{while.context.counter + 1}}",
          "iteration": "{{while.iteration}}"
        }
      }
    }
  ],
  "next": [
    "final_node"
  ]
}
```

**Ожидаемый результат:**
```json
{
  "iterations": 5,
  "final_counter": 5,
  "break_reason": "condition_met"
}
```

## Информация о файле
**Путь:** `dowhile\DoWhileNode.yaml`
