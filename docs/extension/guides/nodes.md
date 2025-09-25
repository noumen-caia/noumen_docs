# Библиотека нод

Расширения могут добавлять библиотеки нод, которые отображаются в Node Assets.

## Добавление в манифест

```json
{
  "contributes": {
    "nodes": {
      "name": "My Node Library",
      "label": "my-nodes",
      "path": "./nodes"
    }
  }
}
```

## Структура папки с нодами

```
/nodes
├── node1/
│   ├── schema.json
│   └── ui.jsx
├── node2/
│   ├── schema.json
│   └── ui.jsx
└── index.json
```

## Схема ноды (schema.json)

```json
{
  "name": "Vector3",
  "data": {
    // некоторые данные
  },
  "ports": [
    {
      "type": "execution",
      "direction": "input",
      "name": "",
      "key": ""
    },
    {
      "type": "execution",
      "direction": "output",
      "name": "",
      "key": ""
    },
    {
      "type": "data",
      "direction": "input",
      "name": "X",
      "key": "x",
      "dataType": "number",
      "defaultValue": 0
    },
    {
      "type": "data",
      "direction": "input",
      "name": "Y",
      "key": "y",
      "dataType": "number",
      "defaultValue": 0
    },
    {
      "type": "data",
      "direction": "input",
      "name": "Z",
      "key": "z",
      "dataType": "number",
      "defaultValue": 0
    },
    {
      "type": "data",
      "direction": "output",
      "name": "Vector",
      "极": "vector",
      "dataType": "object"
    }
  ]
}
```

## UI компонент (ui.jsx)

```jsx
import {
  EditorNode,
  EditorNodeContent,
  EditorNodeHeader,
  EditorNodeInputPorts,
  EditorNodeOutputPorts,
} from "./editor-node";

export default function MyCustomNode({node}) {
  return (
    <EditorNode>
      <EditorNodeHeader />
      <EditorNodeContent>
        <EditorNodeInputPorts />
        <EditorNodeOutputPorts />
      </EditorNodeContent>
    </EditorNode>
  );
}
```

