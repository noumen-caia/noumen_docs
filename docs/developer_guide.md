# Руководство разработчика

## Глоссарий

| Термин | Определение |
|----|----|
| Рабочий процесс (workflow) | Последовательный запуск действий из доступного набора |
| Нода (node) | Базовая единица действия в workflow |
| Контекст  (Context) | Данные, доступные в текущей области видимости |
| Параметр (Parameters) | Статическая настройка ноды |
| Вход/ Выход (Input/Output) | Динамические порты данных |
| Фабрика нод (NodeFactory) | Система создания и выполнения нод |
| BaseNode | Базовый класс для всех нод |

## Построение workflow

### Основные принципы


1. **Логика передачи данных и управления потоком разделены** - данные передаются через соединения, управление через последовательность выполнения
2. **Связи между нодами** представлены шаблонами типа `{{node_uuid.output_key}}`
3. **Динамическая подстановка** значений параметров во время выполнения
4. **Параллельное выполнение** нод без зависимостей

### Структура workflow

```json
{
    "name": "Workflow Name",
    "workflow_id": "unique-id",
    "nodes": [
        {
            "uuid": "node_id",
            "name": "Node Name",
            "type": "NodeType",
            "parameters": {},
            "inputs": {},
            "next": ["next_node_id"]
        }
    ]
}
```

### Передача данных

Используйте шаблоны для передачи данных между нодами:

* `{{node_uuid}}` - весь результат ноды
* `{{node_uuid.key}}` - конкретное поле результата
* `{{node_uuid.[index]}}` - элемент списка по индексу
* `{{node_uuid.key.[index]}}` - комбинированный доступ

## Разработка нод

### Требования к ноде

Каждая нода должна:


1. **Наследоваться от BaseNode**
2. **Иметь методы ____init____() и exec()** - точку входа для выполнения
3. **Определить META** - метаданные ноды
4. **Определять** доступные методы, если их несколько в **NODE_METHODS**
5. **Поддерживать типизацию** входных и выходных данных
6. **Иметь YAML-схему** для фронтенда

### Структура ноды

#### 1. Базовый класс

```python
from node_sdk import BaseNode
from pydantic import BaseModel
from typing import Dict, Any

class MyNode(BaseNode):
    """
    Описание ноды для работы с данными.
    """
    
    META = {
        "name": "MyNode",
        "display_name": "My Node",
        "description": "Описание функциональности ноды",
        "icon": "icon_name",
        "package": "caia_core",
        "version": "1.0.0",
        "deprecated": False,
        "tags": ["Tag1", "Tag2"],
        "category": "Data",
    }
    
    def __init__(self, method: str = None, **kwargs):
        """Инициализация ноды с параметрами"""
        self.method = method
        # Инициализация параметров
    
    def exec(self, task: dict) -> dict:
        """Точка входа для выполнения ноды"""
        # Логика выполнения
        return {"result": "data"}
```

#### 2. Нода с несколькими методами

```python
class DateTimeNode(BaseNode):
    """
    Нода для работы с датой и временем.
    """
    
    META = {
        "name": "DateTimeNode",
        "display_name": "DateTimeNode", 
        "description": "Нода для работы с датой и временем.",
        "icon": "calendar",
        "package": "caia_core",
        "version": "1.0.0",
        "deprecated": False,
        "tags": ["Date", "Time", "Datetime"],
        "category": "DateTime",
    }
    
    NODE_METHODS = ["add", "subtract", "extract", "format", "now", "diff", "round"]
    
    def __init__(self, method: str = None):
        self.method = method
    
    def add(self, params: AddTimeParams) -> str:
        """Добавить время к дате"""
        # Логика добавления времени
        return result_dt.isoformat()
    
    def now(self, params: NowParams) -> str:
        """Получить текущую дату"""
        # Логика получения текущей даты
        return now.isoformat()
    
    def exec(self, task: dict) -> dict:
        """Маршрутизация по методам"""
        mode = task.get("mode") or self.method
        if mode not in self.NODE_METHODS:
            raise ValueError(f"Режим '{mode}' не поддерживается.")
        
        # Вызов соответствующего метода
        return getattr(self, mode)(params)
```

### YAML-схема для фронтенда

Каждая нода должна иметь YAML-файл с описанием для фронтенда:

```yaml
name: DateTimeNode
type: DateTimeNode
language: Python
package: caia_core
version: 1.0.0
icon: calendar
deprecated: false
description: Нода для работы с датой и временем.
tags:
- Date
- Time
- Datetime
category: DateTime
parameters:
  type: object
  properties:
    method:
      type: string
      enum:
      - add
      - subtract
      - extract
      - format
      - now
      - diff
      - round
inputs_schema:
  now:
    type: object
    properties:
      params:
        properties:
          timezone:
            default: UTC
            type: string
          with_time:
            default: true
            type: boolean
        type: object
    required:
    - params
outputs_schema:
  now:
    type: string
```

### Типизация данных

Используйте Pydantic модели для типизации:

```python
from pydantic import BaseModel, Field
from typing import Optional

class NowParams(BaseModel):
    timezone: str = "UTC"
    with_time: bool = True

class AddTimeParams(BaseModel):
    date: str
    years: Optional[int] = None
    months: Optional[int] = None
    days: Optional[int] = None
    hours: Optional[int] = None
    minutes: Optional[int] = None
    seconds: Optional[int] = None
```

### Обработка ошибок

```python
def exec(self, task: dict) -> dict:
    try:
        # Логика выполнения
        return {"result": "success"}
    except Exception as e:
        raise ValueError(f"Ошибка выполнения ноды: {str(e)}")
```

### Примеры существующих нод

#### DateTimeNode - работа с датой и временем

```python
class DateTimeNode(BaseNode):
    """
    Нода для работы с датой и временем.
    """
    
    META = {
        "name": "DateTimeNode",
        "display_name": "DateTimeNode", 
        "description": "Нода для работы с датой и временем.",
        "icon": "calendar",
        "package": "caia_core",
        "version": "1.0.0",
        "deprecated": False,
        "tags": ["Date", "Time", "Datetime"],
        "category": "DateTime",
    }
    
    NODE_METHODS = ["add", "subtract", "extract", "format", "now", "diff", "round"]
    
    def __init__(self, method: str = None):
        self.method = method
    
    def exec(self, task: dict) -> dict:
        """Маршрутизация по методам"""
        mode = task.get("mode") or self.method
        if mode not in self.NODE_METHODS:
            raise ValueError(f"Режим '{mode}' не поддерживается.")
        
        # Вызов соответствующего метода
        return getattr(self, mode)(params)
```

#### HTTPRequestNode - HTTP запросы

```python
class HTTPRequestNode(BaseNode):
    """
    Нода для выполнения HTTP запросов.
    """
    
    META = {
        "name": "HTTPRequestNode",
        "display_name": "HTTPRequestNode",
        "description": "Узел для работы с HTTP запросами",
        "icon": "uuid",
        "package": "caia_core",
        "version": "1.0.0",
        "deprecated": False,
        "tags": ["Data", "HTTP"],
        "category": "Data",
    }
    
    NODE_METHODS = [ 
        'get', 
        'options', 
        'trace', 
        'head', 
        'post',
        'put',
        'patch',
        'delete'
    ]
    
    def __init__(self, method) -> None:
        self.method = method
    
    def get(self, params: BaseRequestModel):
        "GET запрос"
        return httpx.get(**params)
    
    def post(self, params: BodyOrFileRequestModel):
        "POST запрос"
        return httpx.post(**params)
    
    def exec(self, task: dict) -> Any:
        """Вызывает API контейнера для выполнения ноды"""
        try:
            match self.method:
                case 'get':
                    response = self.get(task)
                case 'post':
                    response = self.post(task)
                case _:
                    raise ValueError(
                        f'Неподдерживаемый метод: {self.method}. '
                        f'Доступные методы: {list(self.NODE_METHODS)}'
                    )
            response.raise_for_status()
            return response.json()
        except Exception as e:
            raise ValueError(f"Ошибка выполнения запроса: {str(e)}")
```

### Структура данных ноды

Нода работает с тремя типами данных:

* **Параметры (parameters)** - статические настройки, заданные при создании ноды
* **Входы (inputs)** - динамические данные, передаваемые от других нод
* **Выходы (outputs)** - результат выполнения ноды

### Специальные ноды

#### Ноды маршрутизации

Ноды IF и Switch для условного выполнения. Эти ноды встроены в систему и не требуют разработки.

**Пример конфигурации IfNode:**

```yaml
uuid: if_node1
name: IfNode
type: IfNode
parameters:
  conditions:
    combinator: and
    conditions:
      - operator:
          type: number
          operation: greater_than
        leftValue: '{{ result }}'
        rightValue: 10
inputs:
  result: '{{simple1.outputs.result}}'
next:
  - condition: true
    node_id: edit_field1
  - condition: false
    node_id: edit_field2
```

**Пример конфигурации SwitchNode:**

```yaml
uuid: switch1
name: SwitchNode
type: SwitchNode
parameters:
  rules:
    - operator:
        type: number
        operation: equals
      leftValue: '{{ result }}'
      rightValue: 1
      case: case1
inputs:
  result: '{{simple1.outputs.result}}'
next:
  - case: case1
    node_id: edit_field1
  - case: case2
    node_id: edit_field2
```

#### Ноды циклов

Ноды ForEach и DoWhile для циклического выполнения. Эти ноды встроены в систему.

**Пример конфигурации ForEachNode:**

```yaml
uuid: for_each
name: ForEachNode
type: ForEachNode
parameters:
  async: false
inputs:
  items: '{{parent_node.result}}'
nodes:
  - uuid: process_item
    name: ProcessItem
    type: SomeNode
    # Обработка каждого элемента списка
```

**Пример конфигурации DoWhileNode:**

```yaml
uuid: do_while
name: DoWhileNode
type: DoWhileNode
parameters:
  break_condition: '{{process_step.result}} == "stop"'
  max_iterations: 10
inputs:
  context: '{{parent_node.result}}'
nodes:
  - uuid: process_step
    name: ProcessStep
    type: SomeNode
    # Выполнение до выполнения условия
```

### Лучшие практики


1. **Используйте типизацию** - всегда определяйте Pydantic модели для входных данных
2. **Обрабатывайте ошибки** - возвращайте понятные сообщения об ошибках
3. **Документируйте код** - используйте docstrings для описания методов
4. **Тестируйте ноды** - создавайте unit-тесты для проверки функциональности
5. **Следуйте соглашениям** - используйте стандартные имена и структуры

### Развертывание нод


1. Разместите код ноды в директории `nodes/your_node/`
2. Создайте YAML-схему `YourNode.yaml`