# Статус-бар

API для работы с элементами статус-бара.

## Создание элемента статус-бара

```javascript
export function activate(sdk, context) {
  // Создать элемент в левой части статус-бара
  const leftItem = sdk.window.createStatusBarItem(
    'my-extension-left',
    'left',    // left или right
    100        // приоритет (опционально)
  );

  // Создать элемент в правой части
  const rightItem = sdk.window.createStatusBarItem(
    'my-extension-right',
    'right',
    200
  );

  context.subscriptions.push(leftItem, rightItem);
}
```

## Настройка элемента

```javascript
export function activate(sdk, context) {
  const item = sdk.window.createStatusBarItem('my-item', 'left');

  // Установить текст
  item.text = 'Hello World';

  // Установить команду при клике
  item.command = 'myExtension.showInfo';

  // Показать элемент
  item.show();

  context.subscriptions.push(item);
}
```

## Динамическое обновление

```javascript
export function activate(sdk, context) {
  const item = sdk.window.createStatusBarItem('counter', 'right');
  let count = 0;

  item.text = `Count: ${count}`;
  item.command = 'myExtension.increment';
  item.show();

  // Обновлять при выполнении команды
  context.subscriptions.push(
    sdk.commands.registerCommand('myExtension.increment', () => {
      count++;
      item.text = `Count: ${count}`;
    })
  );

  context.subscriptions.push(item);
}
```

## Скрытие элемента

```javascript
export function activate(sdk, context) {
  const item = sdk.window.createStatusBarItem('conditional-item', 'left');

  item.text = 'Conditional Item';
  item.show();

  // Скрыть через некоторое время
  setTimeout(() => {
    item.hide();
  }, 5000);

  context.subscriptions.push(item);
}
```

## SDK

- `createStatusBarItem(id, alignment, priority?)` - создать элемент
- `text` - текст элемента
- `icon` - иконка элемента
- `command` - команда при клике
- `show()` - показать элемент
- `hide()` - скрыть элемент
