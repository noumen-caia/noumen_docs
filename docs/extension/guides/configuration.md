# Конфигурация

API для работы с настройками расширений и приложения.

## Получение конфигурации

```javascript
export function activate(sdk) {
  // Получить значение конфигурации
  const config = await sdk.workspace.getConfiguration('myExtension');
  const value = config.value;
  
  // Получить конкретную секцию
  const theme = await sdk.workspace.getConfiguration('myExtension.theme');
}
```

## Отслеживание изменений

```javascript
export function activate(sdk, context) {
  // Подписка на изменения конфигурации
  const disposable = sdk.workspace.onDidChangeConfiguration(
    'myExtension',
    (newValue) => {
      console.log('Configuration changed:', newValue);
    }
  );
  
  context.subscriptions.push(disposable);
}
```

## Определение конфигурации

В `package.json` расширения:

```json
{
  "contributes": {
    "configuration": {
      "title": "My Extension",
      "properties": {
        "myExtension.enabled": {
          "type": "boolean",
          "default": true,
          "description": "Enable my extension"
        },
        "myExtension.theme": {
          "type": "string",
          "default": "dark",
          "enum": ["dark", "light"],
          "description": "Theme preference"
        }
      }
    }
  }
}
```

## API SDK

- `getConfiguration(section)` - получение конфигурации
- `onDidChangeConfiguration(section, callback)` - подписка на изменения конфигурации