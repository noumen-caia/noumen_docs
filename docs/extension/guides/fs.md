# Файловая система

API для работы с файлами и папками в Constructor.

## Чтение файлов

```javascript
export function activate(sdk) {
  // Чтение текстового файла
  const content = await sdk.fs.readText('file:///path/to/file.txt');
  
  // Чтение директории
  const entries = await sdk.fs.readDirectory('file:///path/to/directory');
  // entries: [['file1.txt', 1], ['folder', 2]]
}
```

## Запись файлов

```javascript
export function activate(sdk) {
  // Создание файла
  await sdk.fs.writeFile('file:///path/to/new-file.txt', 'Hello World');
  
  // Создание директории
  await sdk.fs.createDirectory('file:///path/to/new-folder');
}
```

## Удаление

```javascript
export function activate(sdk) {
  // Удаление файла или папки
  await sdk.fs.delete('file:///path/to/file.txt');
}
```

## API SDK

- `readText(uri)` - чтение текстового файла
- `writeFile(uri, content)` - запись файла
- `createDirectory(uri)` - создание директории
- `readDirectory(uri)` - чтение директории
- `delete(uri)` - удаление файла/папки
