# 🔧 Исправление ошибки сборки на Netlify

## Проблема
```
error during build:
[vite:build-html] crypto.hash is not a function
```

## Решение

### 1. Обновлена конфигурация Vite
Добавлены настройки в `vite.config.js`:
```javascript
optimizeDeps: {
  include: ['react', 'react-dom', 'react-router-dom']
},
define: {
  global: 'globalThis'
}
```

### 2. Указана конкретная версия Node.js
В `netlify.toml`:
```toml
[build.environment]
  NODE_VERSION = "18.19.0"
```

### 3. Создан файл .nvmrc
```
18.19.0
```

### 4. Добавлены engines в package.json
```json
"engines": {
  "node": ">=18.0.0",
  "npm": ">=9.0.0"
}
```

## Проверка

### Локальная проверка
```bash
npm run build
```

### Результат
✅ Сборка проходит успешно
✅ Все файлы генерируются корректно
✅ Размеры бандла оптимизированы

## Дополнительные рекомендации

### Если проблема повторится:
1. Проверьте логи сборки в Netlify
2. Убедитесь, что все зависимости установлены
3. Попробуйте очистить кэш: `npm run build -- --force`

### Мониторинг
- Следите за обновлениями Vite
- Проверяйте совместимость с Node.js версиями
- Тестируйте сборку перед деплоем 