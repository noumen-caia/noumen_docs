# Extension SDK

SDK — это набор JavaScript API, которые можно вызывать в расширениях Constructor. На этой странице перечислены основные API, доступные разработчикам расширений.

## Команды (Commands)

### `registerCommand(id: string, handler: (...args: any[]) => any): IDisposable`
Регистрирует команду в IDE.

```javascript
context.subscriptions.push(sdk.commands.registerCommand("my-ext.hello", () => {
  console.log("Hello");
}));
```

### `executeCommand(id: string, ...args: any[]): Promise<any>`
Выполняет команду.

### `hasCommand(id: string): boolean`
Проверяет существование команды.

### `getCommands(): Promise<string[]>`
Получает все доступные команды.

## Окна (Windows)

### `showInfoMessage(title: string, message?: string, options?: NotificationOptions): Promise<any>`
Показывает информационное сообщение.

```javascript
sdk.window.showInfoMessage("Payment info", "Your payment was processed successfully");
```

### `showSuccessMessage(title: string, message?: string, options?: NotificationOptions): Promise<any>`
Показывает сообщение об успехе.

### `showWarnMessage(title: string, message?: string, options?: NotificationOptions): Promise<any>`
Показывает предупреждение.

### `showErrorMessage(title: string, message?: string, options?: NotificationOptions): Promise<any>`
Показывает сообщение об ошибке.

## Рабочее пространство (Workspace)

### `getConfiguration(section?: string): Promise<Configuration>`
Получает конфигурацию.

### `onDidChangeConfiguration(section: string, callback: (newValue: any) => void): IDisposable`
Подписывается на изменения конфигурации.

## Файловая система (FS)

### `readText(uri: string): Promise<string>`
Читает текстовый файл.

### `writeFile(uri: string, content: string): Promise<void>`
Записывает файл.

### `createDirectory(uri: string): Promise<void>`
Создает директорию.

### `readDirectory(uri: string): Promise<[string, number][]>`
Читает директорию.

### `delete(uri: string): Promise<void>`
Удаляет файл или папку.

## Редактор узлов (NodeEditor)

### `addNode(node: NodeDefinition): Promise<Node>`
Добавляет ноду.

### `getNode(id: string): Promise<Node>`
Получает ноду.

### `updateNode(id: string, updates: Partial<NodeDefinition>): Promise<void>`
Обновляет ноду.

### `removeNode(id: string): Promise<void>`
Удаляет ноду.

### `getNodes(): Promise<Node[]>`
Получает все ноды.

### `onDidChangeNode(callback: (event: NodeEvent) => void): IDisposable`
Событие изменения ноды.

### `onDidChangeEdge(callback: (event: EdgeEvent) => void): IDisposable`
Событие изменения связи.





