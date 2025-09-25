# CKANNode (`CKANNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | Data |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | Data |

**Описание:** Узел для работы с хранилищем данных CKAN

## Параметры конструктора

- **credentials**: `object` (обяз.). Учётные данные
  - **url**: `string` (обяз.). CKAN url
  - **api_key**: `string` (обяз.). CKAN api key
- **method**: `string (enum: setup_dataset, get_dataset_metadata_by_id, setup_resource, get_resourse_data_by_id, get_resource_metadata_by_name, update_resource)` (обяз.). 
## Входы

### Входы метода `setup_dataset`

- **dataset_name**: `string` (обяз.). названия набора данных
- **dataset_title**: `string` (обяз.). описание набора данных
- **custom_metadata**: `string` (обяз.). метаданные в формате {'key': key, 'value': value}
- **dataset_notes**: `string`. описание набора данных. Defaults to ''.
- **tags**: `array[string]`. теги. Defaults to [{'name':'target'}, {'name':'palmoil'}, {'name':'investing.com'}].
- **owner_org**: `string`. название организации-владельца. Defaults to 'efko'.

### Входы метода `get_dataset_metadata_by_id`

- **dataset_id**: `string` (обяз.). id набора данных

### Входы метода `setup_resource`

- **dataset_id**: `string` (обяз.). id датасета
- **resource_name**: `string` (обяз.). имя ресурса
- **file_format**: `string` (обяз.). формат, например csv, json, xml, xlsx
- **records**: `object` (обяз.). словарь со значениями, можно получить из pd.DataFrame с помощью df.to_dict('records') 
- **fields**: `array[object]`. колонки. Defaults to None.
- **primary_key**: `array[string]`. колонка первичного ключа. Defaults to None.

### Входы метода `get_resourse_data_by_id`

- **resource_id**: `string` (обяз.). id ресурса
- **limit**: `integer`. лимит на чтение за 1 раз. Defaults to 100.
- **q**: `string`. дополнительные запрос-фильтр. Defaults to None.

### Входы метода `get_resource_metadata_by_name`

- **name**: `string` (обяз.). имя ресурса

### Входы метода `update_resource`

- **resource_id**: `string` (обяз.). id ресурса
- **records**: `object` (обяз.). новая версия данных
- **method**: `string`. метод вставки

## Выходы

### Выходы метода `setup_dataset`

- **id**: `string`. 

### Выходы метода `get_dataset_metadata_by_id`

- **items**: `array[object]`. 
  - _Структура элементов объекта не детализирована в схеме._

### Выходы метода `setup_resource`

- **id**: `string`. 

### Выходы метода `get_resourse_data_by_id`

- **items**: `array[object]`. 
  - _Структура элементов объекта не детализирована в схеме._

### Выходы метода `get_resource_metadata_by_name`

- **items**: `array[object]`. 
  - _Структура элементов объекта не детализирована в схеме._

### Выходы метода `update_resource`

- **result**: `object`. 
  - _Структура объекта не детализирована в схеме._

## Примеры вызова через ранер

### Пример 1: Cоздает набор данных в удаленном экземпляре CKAN, добавляет
к нему ресурс хранилища данных и загружает первый дамп.  
Скрипт возвращает идентификатор ресурса.

**Конфигурация ноды:**
```json
{
  "uuid": "ckannode_setup_dataset_example",
  "name": "CKANNode - setup_dataset",
  "type": "CKANNode",
  "parameters": {
    "credentials": {
      "url": "https://example.com",
      "api_key": "{{env.API_KEY}}"
    },
    "method": "setup_dataset"
  },
  "inputs": {
    "dataset_name": "example_value",
    "dataset_title": "example_value",
    "custom_metadata": "{{env.API_TOKEN}}",
    "dataset_notes": "",
    "tags": [
      {
        "name": "target"
      },
      {
        "name": "palmoil"
      },
      {
        "name": "investing.com"
      }
    ],
    "owner_org": "efko"
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
{
  "id": "example_value"
}
```

### Пример 2: Запрос метаданных набора данных

**Конфигурация ноды:**
```json
{
  "uuid": "ckannode_get_dataset_metadata_by_id_example",
  "name": "CKANNode - get_dataset_metadata_by_id",
  "type": "CKANNode",
  "parameters": {
    "credentials": {
      "url": "https://example.com",
      "api_key": "{{env.API_KEY}}"
    },
    "method": "setup_dataset"
  },
  "inputs": {
    "dataset_id": "example_value"
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
[
  {
    "id": 1,
    "name": "Item 1",
    "status": "active"
  },
  {
    "id": 2,
    "name": "Item 2",
    "status": "pending"
  }
]
```

### Пример 3: Создает ресурс хранилища данных

**Конфигурация ноды:**
```json
{
  "uuid": "ckannode_setup_resource_example",
  "name": "CKANNode - setup_resource",
  "type": "CKANNode",
  "parameters": {
    "credentials": {
      "url": "https://example.com",
      "api_key": "{{env.API_KEY}}"
    },
    "method": "setup_dataset"
  },
  "inputs": {
    "dataset_id": "example_value",
    "resource_name": "example_value",
    "file_format": "example_value",
    "records": {
      "key": "value"
    },
    "fields": [
      {
        "id": 1,
        "name": "item1"
      },
      {
        "id": 2,
        "name": "item2"
      }
    ],
    "primary_key": [
      "item1",
      "item2"
    ]
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
{
  "id": "example_value"
}
```

## Информация о файле
**Путь:** `ckan\CKANNode.yaml`
