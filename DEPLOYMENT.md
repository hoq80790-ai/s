# 🚀 Деплой на Netlify

## Подготовка к деплою

### 1. Настройка переменных окружения
Создайте файл `.env.production` в корне проекта:

```env
VITE_APP_TITLE=Telegram Gifts
VITE_APP_VERSION=1.0.0
VITE_API_URL=https://api.example.com
VITE_TELEGRAM_BOT_TOKEN=your_bot_token_here
```

### 2. Проверка конфигурации
Убедитесь, что все файлы настроены правильно:

- ✅ `netlify.toml` - конфигурация Netlify
- ✅ `public/_redirects` - редиректы для SPA
- ✅ `package.json` - скрипты сборки

## Деплой через Netlify CLI

### Установка Netlify CLI
```bash
npm install -g netlify-cli
```

### Логин в Netlify
```bash
netlify login
```

### Инициализация проекта
```bash
netlify init
```

### Сборка и деплой
```bash
npm run build
netlify deploy --prod
```

## Деплой через GitHub

### 1. Подключение репозитория
1. Зайдите на [netlify.com](https://netlify.com)
2. Нажмите "New site from Git"
3. Выберите ваш GitHub репозиторий
4. Настройте параметры сборки:
   - **Build command**: `npm run build`
   - **Publish directory**: `dist`
   - **Node version**: `18`

### 2. Настройка переменных окружения
В настройках сайта на Netlify добавьте переменные окружения:
- `VITE_APP_TITLE`
- `VITE_APP_VERSION`
- `VITE_API_URL`
- `VITE_TELEGRAM_BOT_TOKEN`

### 3. Настройка домена
1. Перейдите в "Domain settings"
2. Настройте кастомный домен или используйте предоставленный Netlify
3. Настройте SSL сертификат

## Проверка деплоя

### Локальная проверка
```bash
npm run build
npm run preview
```

### Проверка на Netlify
1. Откройте ваш сайт
2. Проверьте все функции
3. Проверьте консоль на ошибки
4. Проверьте мобильную версию

## Troubleshooting

### Проблемы с роутингом
Если страницы не загружаются, проверьте файл `public/_redirects`

### Проблемы с переменными окружения
Убедитесь, что все переменные добавлены в настройках Netlify

### Проблемы с Telegram Web App
Проверьте, что домен добавлен в настройках бота

## Оптимизация

### Кэширование
Файл `netlify.toml` настроен для оптимального кэширования статических файлов

### Сжатие
Netlify автоматически сжимает файлы для ускорения загрузки

### CDN
Ваш сайт будет раздаваться через глобальную CDN сеть Netlify