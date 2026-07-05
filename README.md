# Links Manager

SPA для хранения и организации ссылок. Сейчас реализованы лендинг и экран авторизации (вход, регистрация, сброс пароля).

## Стек

| Слой | Технологии |
|------|------------|
| **Фронтенд** | Vue 3, Vite, Vue Router, Pinia, PrimeVue, Tailwind CSS, Zod |
| **Бэкенд** | [Supabase](https://supabase.com/) — аутентификация и база данных (BaaS, отдельного сервера в репозитории нет) |

## Требования

- Node.js `^22.18.0` или `>=24.12.0`
- npm
- Проект Supabase с включённой аутентификацией

## Быстрый старт

```sh
# 1. Установить зависимости
npm install

# 2. Настроить переменные окружения
# Скопируйте .env.example → .env и укажите ключ
# (Supabase → Project Settings → API)

# 3. Запустить dev-сервер
npm run dev
```

Приложение будет доступно по адресу из терминала (обычно `http://localhost:5173`).

> Vite читает `.env` только при старте — после изменения файла перезапустите `npm run dev`.

## Переменные окружения

| Переменная | Описание |
|------------|----------|
| `VITE_SUPABASE_KEY` | Публичный (anon/publishable) ключ Supabase |

URL проекта задаётся в `src/supabase.js`.

## Скрипты

| Команда | Назначение |
|---------|------------|
| `npm run dev` | Dev-сервер с hot-reload |
| `npm run build` | Production-сборка в `dist/` |
| `npm run preview` | Просмотр production-сборки локально |
| `npm run lint` | ESLint + Oxlint |
| `npm run format` | Форматирование через Prettier |

## Структура

```
src/
├── components/AuthForm/   # формы входа, регистрации, сброса пароля
├── composables/           # переиспользуемая логика (toast-уведомления)
├── views/                 # страницы: HomeView, AuthView
├── router/                # маршруты / и /auth
├── stores/                # Pinia
└── supabase.js            # клиент Supabase
```

## Маршруты

- `/` — главная страница
- `/auth` — авторизация (вход / регистрация / восстановление пароля)
