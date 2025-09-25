# Темы

API для работы с темами интерфейса.

## Создание темы

Темы создаются через конфигурацию в `package.json`:

```json
{
  "contributes": {
    "themes": [
      {
        "label": "My Custom Theme",
        "path": "./themes/my-theme.json"
      }
    ]
  }
}
```

## Структура темы

Файл темы `themes/my-theme.json`:

```json
{
	"name": "Dark",
	"type": "dark",
	"colors": {
		"background-100": "#0a0a0a",
		"background-200": "#000000",
		"gray-100": "#1a1a1a",
		"gray-200": "#1f1f1f",
		"gray-300": "#292929",
		"gray-400": "#2e2e2e",
		"gray-500": "#454545",
		"gray-600": "#878787",
		"gray-700": "#8f8f8f",
		"gray-800": "#7d7d7d",
		"gray-900": "#a1a1a1",
		"gray-1000": "#ededed",
		"primary": "#e7006d",
		"primary-foreground": "#ededed"
	}
}
```

## Типы тем

```json
{
    "themes": [
      {
        "label": "Dark",
        "path": "./themes/dark-theme.json"
      },
      {
        "label": "Light",
        "path": "./themes/light-theme.json"
      }
    ]
}
```
