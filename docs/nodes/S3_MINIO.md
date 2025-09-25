# S3/MINIO (`S3/MINIO`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | storage |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | S3, Storage, Minio |

**Описание:** Нода для взаимодействия с S3-совместимым хранилищем (например, MinIO).      Позволяет выполнять основные операции над файлами, папками и бакетами:      загрузку, скачивание, удаление файлов, создание и удаление бакетов, а также проверку и листинг содержимого.

## Параметры конструктора

- **credentials**: `object` (обяз.). 
  - **endpoint**: `string` (обяз.). 
  - **access_key**: `string` (обяз.). 
  - **secret_key**: `string` (обяз.). 
  - **secure**: `Union[string, null]`. 
- **method**: `string (enum: file_upload, file_download, file_delete, file_exists, file_list_objects, bucket_create, bucket_delete, bucket_exists, bucket_list, folder_delete, folder_exists, folder_list_folders)` (обяз.). 
## Входы

### Входы метода `file_upload`

- **bucket_name**: `string` (обяз.). Название бакета.
- **file_path**: `string` (обяз.). Путь к локальному файлу.
- **s3_filepath**: `string` (обяз.). Имя файла/путь в хранилище.

### Входы метода `file_download`

- **bucket_name**: `string` (обяз.). Название бакета.
- **file_path**: `string` (обяз.). Путь, куда сохранить файл локально.
- **s3_filepath**: `string` (обяз.). Путь/имя файла в хранилище.

### Входы метода `file_delete`

- **bucket_name**: `string` (обяз.). Название бакета.
- **s3_filepaths**: `Union[array[string], string]` (обяз.). Список или строка с путём/именем файла(ов) в хранилище.

### Входы метода `file_exists`

- **bucket_name**: `string` (обяз.). Название бакета.
- **s3_filepath**: `string` (обяз.). Путь/имя файла в хранилище.

### Входы метода `file_list_objects`

- **bucket_name**: `string` (обяз.). Название бакета.
- **prefix**: `string`. Папка/префикс поиска (опционально).
- **recursive**: `boolean`. Искать рекурсивно (по всем подпапкам, по умолчанию False).

### Входы метода `bucket_create`

- **bucket_name**: `string` (обяз.). Название бакета.
- **location**: `string`. Локация бакета (опционально).
- **object_lock**: `boolean`. Включить блокировку объектов (опционально).

### Входы метода `bucket_delete`

- **bucket_name**: `string` (обяз.). Название бакета.

### Входы метода `bucket_exists`

- **bucket_name**: `string` (обяз.). Название бакета.

### Входы метода `bucket_list`

- **result**: `object`. Получить список всех бакетов в хранилище.
  - _Структура объекта не детализирована в схеме._

### Входы метода `folder_delete`

- **bucket_name**: `string` (обяз.). Название бакета.
- **folder_path**: `string` (обяз.). Путь к папке (например, "images/").

### Входы метода `folder_exists`

- **bucket_name**: `string` (обяз.). Название бакета.
- **folder_path**: `string` (обяз.). Путь к папке (например, "images/").

### Входы метода `folder_list_folders`

- **bucket_name**: `string` (обяз.). Название бакета.
- **folder_path**: `string` (обяз.). Путь к родительской папке (например, "images/").

## Выходы

### Выходы метода `file_upload`

- **status**: `boolean`. 
- **s3_filepath**: `string`. 
- **error**: `Union[string, null]`. 

### Выходы метода `file_download`

- **status**: `boolean`. 
- **file_path**: `string`. 

### Выходы метода `file_delete`

- **status**: `boolean`. 
- **error**: `Union[string, null]`. 

### Выходы метода `file_exists`

- **status**: `boolean`. 
- **error**: `Union[string, null]`. 

### Выходы метода `file_list_objects`

- **status**: `boolean`. 
- **error**: `Union[string, null]`. 

### Выходы метода `bucket_create`

- **bucket_name**: `string`. 

### Выходы метода `bucket_delete`

- **status**: `boolean`. 
- **error**: `Union[string, null]`. 

### Выходы метода `bucket_exists`

- **status**: `boolean`. 
- **error**: `Union[string, null]`. 

### Выходы метода `bucket_list`

- **items**: `array[string]`. 

### Выходы метода `folder_delete`

- **status**: `boolean`. 
- **error**: `Union[string, null]`. 

### Выходы метода `folder_exists`

- **status**: `boolean`. 
- **error**: `Union[string, null]`. 

### Выходы метода `folder_list_folders`

- **items**: `array[string]`. 

## Примеры вызова через ранер

### Пример 1: Загрузка локального файла в выбранный бакет хранилища.

**Конфигурация ноды:**
```json
{
  "uuid": "s3/minio_file_upload_example",
  "name": "S3/MINIO - file_upload",
  "type": "S3/MINIO",
  "parameters": {
    "credentials": {
      "endpoint": "example_value",
      "access_key": "example_value",
      "secret_key": "example_value"
    },
    "method": "file_upload"
  },
  "inputs": {
    "bucket_name": "example_value",
    "file_path": "example_value",
    "s3_filepath": "example_value"
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
{
  "status": true,
  "s3_filepath": "example_value",
  "error": "example_value"
}
```

### Пример 2: Скачивание файла из хранилища в локальное хранилище.

**Конфигурация ноды:**
```json
{
  "uuid": "s3/minio_file_download_example",
  "name": "S3/MINIO - file_download",
  "type": "S3/MINIO",
  "parameters": {
    "credentials": {
      "endpoint": "example_value",
      "access_key": "example_value",
      "secret_key": "example_value"
    },
    "method": "file_upload"
  },
  "inputs": {
    "bucket_name": "example_value",
    "file_path": "example_value",
    "s3_filepath": "example_value"
  },
  "next": [
    "next_node_id"
  ]
}
```

**Ожидаемый результат:**
```json
{
  "status": true,
  "file_path": "example_value"
}
```

### Пример 3: Удаление одного или нескольких файлов из выбранного бакета.

**Конфигурация ноды:**
```json
{
  "uuid": "s3/minio_file_delete_example",
  "name": "S3/MINIO - file_delete",
  "type": "S3/MINIO",
  "parameters": {
    "credentials": {
      "endpoint": "example_value",
      "access_key": "example_value",
      "secret_key": "example_value"
    },
    "method": "file_upload"
  },
  "inputs": {
    "bucket_name": "example_value",
    "s3_filepaths": [
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
  "status": true,
  "error": "example_value"
}
```

## Информация о файле
**Путь:** `s3\S3Node.yaml`
