# Команды

Команды запускают действия. Они используются для:
- Выполнения пользовательских действий
- Интеграции с UI элементами
- Реализации внутренней логики расширений

## Регистрация команды

```javascript
export function activate(sdk, context) {
  const command = 'myExtension.sayHello';

  const commandHandler = (name = 'world') => {
    console.log(`Hello ${name}!!!`);
  };

  context.subscriptions.push(
    sdk.commands.registerCommand(command, commandHandler)
  );
}
```

## Публикация команды

Чтобы команда появилась в палитре команд, добавьте ее в манифест расширения:

```json
{
  "contributes": {
    "commands": [
      {
        "command": "myExtension.sayHello",
        "title": "Say Hello"
      }
    ]
  }
}
```

## Выполнение команды

```javascript
// Выполнить команду программно
await sdk.commands.executeCommand('myExtension.sayHello', 'John');

// Проверить существование команды
if (sdk.commands.hasCommand('myExtension.sayHello')) {
  // команда существует
}

// Получить все команды
const commands = sdk.commands.getCommands();
```

## API SDK

- `registerCommand(id, handler)` - регистрация команды
- `executeCommand(id, ...args)` - выполнение команды
- `hasCommand(id)` - проверка существования команды
- `getCommands()` - получение всех доступных команд