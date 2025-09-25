# RssFeedReadNode (`RssFeedReadNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data, RSS |

**Описание:** Узел для чтения данных из RSS-лент с поддержкой различных источников.

## Параметры конструктора

- **method**: `string (enum: read)`. 
- **timeout**: `integer`. . По умолчанию: `10`
## Входы

### Входы метода `read`

- **params**: `object` (обяз.). Параметры для чтения RSS ленты.
  - **url**: `string` (обяз.). URL RSS-ленты для чтения
  - **ignoreSSL**: `boolean` (обяз.). Игнорировать ошибки SSL

## Выходы

### Выходы метода `read`

- **items**: `array[object]`. Список статей из RSS ленты

## Примеры вызова через ранер

### Пример 1: Читать RSS ленту по URL.

**Конфигурация ноды:**
```json
{
  "uuid": "rssfeedreadnode_read_example",
  "name": "RssFeedReadNode - read",
  "type": "RssFeedReadNode",
  "parameters": {},
  "inputs": {
    "params": {
      "url": "https://example.com",
      "ignoreSSL": false
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
**Путь:** `rss_feed_read\RssFeedReadNode.yaml`
