# Уведомления

API для показа уведомлений пользователю.

## Типы уведомлений

```javascript
export function activate(sdk) {
  // Информационное уведомление
  await sdk.window.showInfoMessage('Operation completed', 'Info message');
  
  // Успешное уведомление
  await sdk.window.showSuccessMessage('File saved', 'File saved successfully');
  
  // Предупреждение
  await sdk.window.showWarnMessage('Warning', 'This action cannot be undone');
  
  // Ошибка
  await sdk.window.showErrorMessage('Error', 'Something went wrong');
}
```

## Опции уведомлений

```javascript
export function activate(sdk) {
  const options = {
    modal: true,           // Модальное окно
    detail: 'Details...',  // Дополнительная информация
    actions: [             // Кнопки действий
      { label: 'OK', value: 'ok' },
      { label: 'Cancel', value: 'cancel' }
    ]
  };

  const result = await sdk.window.showInfoMessage(
    'Confirm action',
    'Are you sure?',
    options
  );
}
```

## Обработка результата

```javascript
export function activate(sdk) {
  const result = await sdk.window.showInfoMessage(
    'Choose an option',
    'What would you like to do?',
    {
      actions: [
        { label: 'Save', value: 'save' },
        { label: 'Discard', value: 'discard' },
        { label: 'Cancel', value: 'cancel' }
      ]
    }
  );

  switch (result) {
    case 'save':
      console.log('User chose to save');
      break;
    case 'discard':
      console.log('User chose to discard');
      break;
    case 'cancel':
      console.log('User cancelled');
      break;
  }
}
```

## API

- `showInfoMessage(title, message?, options?)` - информационное уведомление
- `showSuccessMessage(title, message?, options?)` - успешное уведомление
- `showWarnMessage(title, message?, options?)` - предупреждение
- `showErrorMessage(title, message?, options?)` - ошибка
