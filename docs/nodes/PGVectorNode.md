# PGVectorNode (`PGVectorNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data, PG, VectorStore |

**Описание:** Узел для работы с векторной базой данных PostgreSQL

## Параметры конструктора

- **credentials**: `object` (обяз.). Данные БД
  - **dbname**: `string` (обяз.). 
  - **user**: `string` (обяз.). 
  - **password**: `string` (обяз.). 
  - **host**: `string` (обяз.). 
  - **port**: `integer` (обяз.). 
  - **autocommit**: `boolean` (обяз.). 
- **method**: `string (enum: check_connection, check_table, create_table, store_documents, query_documents)` (обяз.). 
## Входы

### Входы метода `check_connection`

- **result**: `object`. Проверяет подключение к базе данных
  - _Структура объекта не детализирована в схеме._

### Входы метода `check_table`

- **table**: `string` (обяз.). Имя таблицы для проверки
- **schema**: `string`. Имя схемы. Defaults to 'public'

### Входы метода `create_table`

- **table**: `string`. Имя таблицы. Defaults to 'chunks'.
- **schema**: `string`. Имя схемы. Defaults to 'public'.
- **embedding_dim**: `integer`. Размерность вектора. Defaults to 768.
- **index_type**: `string`. Тип индекса. Defaults to 'hnsw'.

### Входы метода `store_documents`

- **documents**: `array[string]` (обяз.). Список фрагментов текста
- **table**: `string`. Имя таблицы. Defaults to 'chunks'.
- **schema**: `string`. Имя схемы. Defaults to 'public'.

### Входы метода `query_documents`

- **embeddings**: `array[number]` (обяз.). Вектор для поиска
- **table**: `string`. Имя таблицы. Defaults to 'chunks'.
- **schema**: `string`. Имя схемы. Defaults to 'public'.
- **n**: `integer`. Количество результатов. Defaults to 5.
- **k**: `integer`. Количество ближайших соседей. Defaults to 0.

## Выходы

### Выходы метода `check_connection`

- **result**: `string`. 

### Выходы метода `check_table`

- **result**: `string`. 

### Выходы метода `create_table`

- **messages**: `array[unknown]`. 
- **status**: `string`. 

### Выходы метода `store_documents`

- **messages**: `array[unknown]`. 
- **status**: `string`. 

### Выходы метода `query_documents`

- **items**: `array[object]`. 
  - **Структура элементов массива:**
    - **page_content**: `string`. 
    - **metadata**: `object`. 
    - **embeddings**: `Union[array[number], null]`. 

## Примеры вызова через ранер

### Пример 1: Проверяет подключение к базе данных

**Конфигурация ноды:**
```json
{
  "uuid": "pgvectornode_check_connection_example",
  "name": "PGVectorNode - check_connection",
  "type": "PGVectorNode",
  "parameters": {
    "credentials": {
      "dbname": "example_value",
      "user": "user@example.com",
      "password": "{{env.API_KEY}}",
      "host": "https://example.com",
      "port": 8080,
      "autocommit": true
    },
    "method": "check_connection"
  },
  "inputs": {},
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
"example_result"
```

### Пример 2: Проверяет существование таблицы в базе данных

**Конфигурация ноды:**
```json
{
  "uuid": "pgvectornode_check_table_example",
  "name": "PGVectorNode - check_table",
  "type": "PGVectorNode",
  "parameters": {
    "credentials": {
      "dbname": "example_value",
      "user": "user@example.com",
      "password": "{{env.API_KEY}}",
      "host": "https://example.com",
      "port": 8080,
      "autocommit": true
    },
    "method": "check_connection"
  },
  "inputs": {
    "table": "example_value",
    "schema": "public"
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
"example_result"
```

### Пример 3: Создает таблицу в векторной базе данных PostgreSQL

**Конфигурация ноды:**
```json
{
  "uuid": "pgvectornode_create_table_example",
  "name": "PGVectorNode - create_table",
  "type": "PGVectorNode",
  "parameters": {
    "credentials": {
      "dbname": "example_value",
      "user": "user@example.com",
      "password": "{{env.API_KEY}}",
      "host": "https://example.com",
      "port": 8080,
      "autocommit": true
    },
    "method": "check_connection"
  },
  "inputs": {
    "table": "chunks",
    "schema": "public",
    "embedding_dim": 768,
    "index_type": "hnsw"
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
{
  "messages": [
    "item1",
    "item2"
  ],
  "status": "example_value"
}
```

## Информация о файле
**Путь:** `pgvector\PGVectorNode.yaml`
