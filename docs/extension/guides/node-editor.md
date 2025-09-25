# Редактор нод

API для работы с редактором нод.

## Добавление нод

```javascript
export function activate(sdk) {
  // Добавить ноду в редактор
  const node = await sdk.nodeEditor.addNode({
    id: 'my-node-1',
    type: 'custom-node',
    position: { x: 100, y: 100 },
    data: { label: 'My Custom Field Value' },
    ports: [
      { id: 'input-1', type: 'execution', direction: 'input', name: 'Input' },
      { id: 'output-1', type: 'data', direction: 'output', name: 'Output' }
    ]
  });
}
```

## Управление нодами

```javascript
export function activate(sdk) {
  // Получить все ноды
  const nodes = await sdk.nodeEditor.getNodes();
  
  // Получить конкретную ноду
  const node = await sdk.nodeEditor.getNode('node-id');
  
  // Обновить ноду
  await sdk.nodeEditor.updateNode('node-id', {
    data: { label: 'Updated Label' }
  });
  
  // Удалить ноду
  await sdk.nodeEditor.removeNode('node-id');
}
```


## События нод

```javascript
export function activate(sdk, context) {
  // Событие изменения ноды
  const nodeDisposable = sdk.nodeEditor.onDidChangeNode((event) => {
    console.log('Node changed:', event);
  });
  
  // Событие изменения связи
  const edgeDisposable = sdk.nodeEditor.onDidChangeEdge((event) => {
    console.log('Edge changed:', event);
  });
  
  context.subscriptions.push(nodeDisposable, edgeDisposable);
}
```

## API SDK

- `addNode(node)` - добавить ноду
- `getNode(id)` - получить ноду
- `updateNode(id, updates)` - обновить ноду
- `removeNode(id)` - удалить ноду
- `getNodes()` - получить все ноды
- `createNodeType(id, code)` - создать тип ноды
- `onDidChangeNode(callback)` - событие изменения ноды
- `onDidChangeEdge(callback)` - событие изменения связи