# Quick Input

API для создания диалогов быстрого ввода.

## Поле ввода

```javascript
export function activate(s极dk) {
  // Показать поле ввода
  const input = await sdk.window.showInputBox({
    prompt: 'Enter your name',
    placeholder: 'John Doe',
    value: 'Default value'
  });
  
  console.log('User entered:', input);
}
```

## Выбор из списка

```javascript
export function activate(sdk) {
  const items = [
    { label: 'Option 1', value: 'opt1' },
    { label: 'Option 2', value: 'opt2' },
    { label: 'Option 3', value: 'opt3' }
  ];

  const selected = await sdk.window.showQuickPick(items, {
    title: 'Choose an option',
    canPickMany: false
  });
  
  console.log('Selected:', selected);
}
```

## Множественный выбор

```javascript
export function activate(sdk) {
  const items = [
    { label: 'Item 1', value: 'item1' },
    { label: 'Item 2', value: 'item2' },
    { label: 'Item 3', value: 'item3' }
  ];

  const selected = await sdk.window.showQuickPickMany(items, {
    title: 'Choose multiple items'
  });
  
  console.log('Selected items:', selected);
}
```

## Опции ввода

```javascript
const inputOptions = {
  placeholder: 'Placeholder text',
  value: 'Default value',
  password: true,         // Скрыть ввод
};

const result = await sdk.window.showInputBox(inputOptions);
```

## Опции выбора

```javascript
const pickOptions = {
  title: 'Choose option',
  canPickMany: false,
};

const result = await sdk.window.showQuickPick(items, pickOptions);
```

## SDK

- `showInputBox(options?)` - поле ввода
- `showQuickPick(items, options?)` - выбор одного элемента
- `showQuickPickMany(items, options?)` - выбор нескольких элементов