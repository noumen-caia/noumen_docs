# SQLQueryBuilderNode (`SQLQueryBuilderNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Database |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | DB, SQL, Ibis |

**Описание:** Универсальная нода для работы с БД через Ibis framework

## Параметры конструктора

- **method**: `string (enum: connect, list_tables, describe_table, build_query, compile, execute, raw_sql, introspect, create_table)`. 
- **timeout**: `integer`. . По умолчанию: `30`
## Входы

### Входы метода `connect`

- **params**: `object` (обяз.). 
  - **url**: `string` (обяз.). Строка подключения к БД
  - **backend**: `Union[string, null]`. Тип БД

### Входы метода `list_tables`

- **params**: `object` (обяз.). 

### Входы метода `describe_table`

- **params**: `object` (обяз.). 
  - **table_name**: `string` (обяз.). Имя таблицы

### Входы метода `build_query`

- **params**: `object` (обяз.). 
  - **table_name**: `string` (обяз.). Имя таблицы
  - **select**: `Union[array[string], null]`. Список полей для SELECT
  - **where**: `Union[object, null]`. Условия фильтрации
  - **group_by**: `Union[array[string], null]`. Поля для группировки
  - **aggregate**: `Union[object, null]`. Агрегатные функции
  - **order_by**: `Union[array[string], null]`. Поля для сортировки
  - **limit**: `Union[integer, null]`. Лимит строк
  - **offset**: `Union[integer, null]`. Смещение

### Входы метода `compile`

- **params**: `object` (обяз.). 
  - **query_params**: `unknown` (обяз.). Параметры запроса

### Входы метода `execute`

- **params**: `object` (обяз.). 
  - **query_params**: `unknown` (обяз.). Параметры запроса
  - **output_format**: `string` (обяз.). Формат вывода

### Входы метода `raw_sql`

- **params**: `object` (обяз.). 
  - **sql**: `string` (обяз.). SQL-запрос
  - **params**: `Union[object, null]`. Параметры для биндинга

### Входы метода `introspect`

- **params**: `object` (обяз.). 

### Входы метода `create_table`

- **params**: `object` (обяз.). 
  - **table_name**: `string` (обяз.). Имя создаваемого объекта
  - **table_type**: `string` (обяз.). Тип объекта: view, materialized_view, table
  - **main_table**: `string` (обяз.). Основная таблица
  - **joins**: `Union[array[object], null]`. Список JOIN операций (None = без JOIN)
  - **select**: `Union[array[string], null]`. Список полей для SELECT
  - **where**: `Union[object, null]`. Условия фильтрации
  - **group_by**: `Union[array[string], null]`. Поля для группировки
  - **order_by**: `Union[array[string], null]`. Поля для сортировки
  - **limit**: `Union[integer, null]`. Лимит строк
  - **offset**: `Union[integer, null]`. Смещение
  - **aggregate**: `Union[object, null]`. Агрегатные функции
  - **database**: `Union[string, null]`. База данных
  - **overwrite**: `boolean` (обяз.). Перезаписать существующий объект
  - **transformations**: `Union[object, null]`. Трансформации колонок
  - **engine**: `Union[string, null]`. Движок таблицы (для ClickHouse)
  - **partition_by**: `Union[string, null]`. Партиционирование
  - **order_by_columns**: `Union[array[string], null]`. Колонки для ORDER BY

## Выходы

### Выходы метода `connect`

- **data**: `unknown`. Данные результата
- **sql**: `Union[string, null]`. Сгенерированный SQL
- **error**: `Union[string, null]`. Ошибка выполнения

### Выходы метода `list_tables`

- **data**: `unknown`. Данные результата
- **sql**: `Union[string, null]`. Сгенерированный SQL
- **error**: `Union[string, null]`. Ошибка выполнения

### Выходы метода `describe_table`

- **data**: `unknown`. Данные результата
- **sql**: `Union[string, null]`. Сгенерированный SQL
- **error**: `Union[string, null]`. Ошибка выполнения

### Выходы метода `build_query`

- **data**: `unknown`. Данные результата
- **sql**: `Union[string, null]`. Сгенерированный SQL
- **error**: `Union[string, null]`. Ошибка выполнения

### Выходы метода `compile`

- **data**: `unknown`. Данные результата
- **sql**: `Union[string, null]`. Сгенерированный SQL
- **error**: `Union[string, null]`. Ошибка выполнения

### Выходы метода `execute`

- **data**: `unknown`. Данные результата
- **sql**: `Union[string, null]`. Сгенерированный SQL
- **error**: `Union[string, null]`. Ошибка выполнения

### Выходы метода `raw_sql`

- **data**: `unknown`. Данные результата
- **sql**: `Union[string, null]`. Сгенерированный SQL
- **error**: `Union[string, null]`. Ошибка выполнения

### Выходы метода `introspect`

- **tables**: `array[string]`. Список таблиц
- **error**: `Union[string, null]`. Ошибка выполнения

### Выходы метода `create_table`

- **data**: `unknown`. Данные результата
- **sql**: `Union[string, null]`. Сгенерированный SQL
- **error**: `Union[string, null]`. Ошибка выполнения

## Примеры вызова через ранер

### Пример 1: None

**Конфигурация ноды:**
```json
{
  "uuid": "sqlquerybuildernode_connect_example",
  "name": "SQLQueryBuilderNode - connect",
  "type": "SQLQueryBuilderNode",
  "parameters": {},
  "inputs": {
    "params": {
      "url": "example_value"
    }
  },
  "next": [
    "next_node_id"
  ]
}
```

### Пример 2: None

**Конфигурация ноды:**
```json
{
  "uuid": "sqlquerybuildernode_list_tables_example",
  "name": "SQLQueryBuilderNode - list_tables",
  "type": "SQLQueryBuilderNode",
  "parameters": {},
  "inputs": {
    "params": {}
  },
  "next": [
    "next_node_id"
  ]
}
```

### Пример 3: None

**Конфигурация ноды:**
```json
{
  "uuid": "sqlquerybuildernode_describe_table_example",
  "name": "SQLQueryBuilderNode - describe_table",
  "type": "SQLQueryBuilderNode",
  "parameters": {},
  "inputs": {
    "params": {
      "table_name": "example_value"
    }
  },
  "next": [
    "next_node_id"
  ]
}
```

## Информация о файле
**Путь:** `sql_query_builder\SQLQueryBuilderNode.yaml`
