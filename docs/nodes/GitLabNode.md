# GitLabNode (`GitLabNode`)

| Параметр | Значение |
|---|---|
| **Версия** | 1.0.0 |
| **Категория** | DevOps |
| **Пакет** | `caia_core` |
| **Статус** | активная |
| **Теги** | GitLab, DevOps |

**Описание:** Узел для административного управления GitLab: группы, проекты, участники, MR, пайплайны

## Параметры конструктора

- **credentials**: `object` (обяз.). 
  - **url**: `string` (обяз.). 
  - **private_token**: `string` (обяз.). 
  - **oauth_token**: `Union[string, null]`. 
  - **ssl_verify**: `boolean` (обяз.). 
- **method**: `string (enum: create_group, group_exists, list_groups, create_project, add_group_member, remove_group_member, list_group_members, add_project_member, remove_project_member, list_project_members, get_user, list_users, create_mr, list_mrs, get_mr, merge_mr, trigger_pipeline, get_pipeline_status)` (обяз.). 
## Входы

### Входы метода `create_group`

- **name**: `string` (обяз.). 
- **path**: `string` (обяз.). 
- **parent_id**: `integer`. 

### Входы метода `group_exists`

- **group_id**: `integer`. 
- **path**: `string`. 

### Входы метода `list_groups`

- **result**: `object`. None
  - _Структура объекта не детализирована в схеме._

### Входы метода `create_project`

- **group_id**: `integer` (обяз.). 
- **name**: `string` (обяз.). 
- **path**: `string`. 

### Входы метода `add_group_member`

- **group_id**: `integer` (обяз.). 
- **user_email**: `string`. 
- **user_id**: `integer`. 
- **role**: `string`. 
- **access_level**: `integer`. 

### Входы метода `remove_group_member`

- **group_id**: `integer` (обяз.). 
- **user_email**: `string`. 
- **user_id**: `integer`. 

### Входы метода `list_group_members`

- **group_id**: `integer` (обяз.). 

### Входы метода `add_project_member`

- **project_id**: `integer` (обяз.). 
- **user_email**: `string`. 
- **user_id**: `integer`. 
- **role**: `string`. 
- **access_level**: `integer`. 

### Входы метода `remove_project_member`

- **project_id**: `integer` (обяз.). 
- **user_email**: `string`. 
- **user_id**: `integer`. 

### Входы метода `list_project_members`

- **project_id**: `integer` (обяз.). 

### Входы метода `get_user`

- **email**: `string` (обяз.). 

### Входы метода `list_users`

- **search**: `string`. 

### Входы метода `create_mr`

- **project_id**: `integer` (обяз.). 
- **source_branch**: `string` (обяз.). 
- **target_branch**: `string` (обяз.). 
- **title**: `string`. 

### Входы метода `list_mrs`

- **project_id**: `integer` (обяз.). 

### Входы метода `get_mr`

- **project_id**: `integer` (обяз.). 
- **mr_iid**: `integer` (обяз.). 

### Входы метода `merge_mr`

- **project_id**: `integer` (обяз.). 
- **mr_iid**: `integer` (обяз.). 

### Входы метода `trigger_pipeline`

- **project_id**: `integer` (обяз.). 
- **ref**: `string`. 
- **variables**: `string`. 

### Входы метода `get_pipeline_status`

- **project_id**: `integer` (обяз.). 
- **pipeline_id**: `integer` (обяз.). 

## Выходы

### Выходы метода `create_group`

- **result**: `string`. 

### Выходы метода `group_exists`

- **result**: `string`. 

### Выходы метода `list_groups`

- **items**: `array[string]`. 

### Выходы метода `create_project`

- **result**: `string`. 

### Выходы метода `add_group_member`

- **result**: `string`. 

### Выходы метода `remove_group_member`

- **result**: `string`. 

### Выходы метода `list_group_members`

- **items**: `array[string]`. 

### Выходы метода `add_project_member`

- **result**: `string`. 

### Выходы метода `remove_project_member`

- **result**: `string`. 

### Выходы метода `list_project_members`

- **items**: `array[string]`. 

### Выходы метода `get_user`

- **result**: `string`. 

### Выходы метода `list_users`

- **items**: `array[string]`. 

### Выходы метода `create_mr`

- **result**: `string`. 

### Выходы метода `list_mrs`

- **items**: `array[string]`. 

### Выходы метода `get_mr`

- **result**: `string`. 

### Выходы метода `merge_mr`

- **result**: `string`. 

### Выходы метода `trigger_pipeline`

- **result**: `string`. 

### Выходы метода `get_pipeline_status`

- **result**: `string`. 

## Примеры вызова через ранер

### Пример 1: None

**Конфигурация ноды:**
```json
{
  "uuid": "gitlabnode_create_group_example",
  "name": "GitLabNode - create_group",
  "type": "GitLabNode",
  "parameters": {
    "credentials": {
      "url": "example_value",
      "private_token": "example_value",
      "ssl_verify": true
    },
    "method": "create_group"
  },
  "inputs": {
    "name": "example_value",
    "path": "example_value",
    "parent_id": 1
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

### Пример 2: None

**Конфигурация ноды:**
```json
{
  "uuid": "gitlabnode_group_exists_example",
  "name": "GitLabNode - group_exists",
  "type": "GitLabNode",
  "parameters": {
    "credentials": {
      "url": "example_value",
      "private_token": "example_value",
      "ssl_verify": true
    },
    "method": "create_group"
  },
  "inputs": {
    "group_id": 1,
    "path": "example_value"
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

### Пример 3: None

**Конфигурация ноды:**
```json
{
  "uuid": "gitlabnode_list_groups_example",
  "name": "GitLabNode - list_groups",
  "type": "GitLabNode",
  "parameters": {
    "credentials": {
      "url": "example_value",
      "private_token": "example_value",
      "ssl_verify": true
    },
    "method": "create_group"
  },
  "inputs": {},
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
  },
  {
    "id": 3,
    "name": "Item 3",
    "status": "completed"
  }
]
```

## Информация о файле
**Путь:** `gitlab\GitLabNode.yaml`
