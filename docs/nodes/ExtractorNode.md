# ExtractorNode (`ExtractorNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data, Loader |

**Описание:** Узел для извлечения данных по web_url

## Параметры конструктора

- _Параметры не требуются._
## Входы

- **web_url**: `Union[string, array[string]]`. строка с URL
- **max_characters**: `integer`. Максимальное количество символов во фрагменте текста. Defaults to 4000
- **overlap**: `integer`. Перекрытие. Defaults to 500
## Выходы

- **messages**: `array[unknown]`. 
- **documents**: `array[unknown]`. 
## Примеры вызова через ранер

### Пример 1: Выполнение ExtractorNode

**Конфигурация ноды:**
```json
{
  "uuid": "extractornode_example",
  "name": "ExtractorNode Example",
  "type": "ExtractorNode",
  "parameters": {},
  "inputs": {
    "web_url": "https://example.com",
    "max_characters": 4000.0,
    "overlap": 500.0
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
{
  "status": "success",
  "data": {
    "processed": 3,
    "failed": 0,
    "results": [
      {
        "id": 1,
        "status": "completed"
      },
      {
        "id": 2,
        "status": "completed"
      }
    ]
  },
  "metadata": {
    "timestamp": "2024-01-15T14:30:00Z",
    "version": "1.0.0"
  }
}
```

## Информация о файле
**Путь:** `extractor\ExtractorNode.yaml`
