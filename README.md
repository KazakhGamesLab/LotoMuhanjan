# 🎲 LotoMuhanjan

> **Классическая игра "Лото" в современной реализации**  
> Telegram Bot + Vue 3 + FastAPI + PostgreSQL

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/python-3.12+-blue.svg)](https://www.python.org/downloads/)
[![Vue](https://img.shields.io/badge/vue-3.4+-green.svg)](https://vuejs.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115+-red.svg)](https://fastapi.tiangolo.com/)

---

## 📖 Описание проекта

**LotoMuhanjan** — это полнофункциональная реализация классической игры "Лото" с современным стеком технологий. Проект включает в себя:

- 🤖 **Telegram Bot** на Aiogram 3.x для взаимодействия с пользователями
- 🎨 **Веб-интерфейс** на Vue 3 с поддержкой Telegram Web Apps
- ⚡ **Backend API** на FastAPI с асинхронной архитектурой
- 🗄️ **PostgreSQL** для хранения данных

Проект демонстрирует контрактную архитектуру с полной типобезопасностью от бэкенда до фронтенда.

---

## ✨ Особенности

- 🔒 **Типобезопасность** — полная поддержка TypeScript от бэкенда до фронтенда
- 🚀 **Высокая производительность** — асинхронный бэкенд на FastAPI
- 📱 **Telegram Web Apps** — интеграция с Telegram Mini Apps
- 🎯 **RESTful API** — четко структурированные эндпоинты с документацией
- 🧪 **Тестируемость** — модульная архитектура для легкого тестирования

---

## 🏗️ Архитектура

```
┌─────────────────────────────────────────────────────┐
│                  Telegram Bot                        │
│              (Aiogram 3.x + Webhook)                │
└──────────────────────┬──────────────────────────────┘
                       │
                       ↓
┌─────────────────────────────────────────────────────┐
│              Telegram Web Apps                       │
│              (Vue 3 + TypeScript)                    │
└──────────────────────┬──────────────────────────────┘
                       │
                       ↓
┌─────────────────────────────────────────────────────┐
│                 Backend API                          │
│           (FastAPI + SQLAlchemy)                     │
└──────────────────────┬──────────────────────────────┘
                       │
                       ↓
┌─────────────────────────────────────────────────────┐
│                  PostgreSQL                          │
│                  (asyncpg)                           │
└─────────────────────────────────────────────────────┘
```

---

## 📁 Структура проекта

```
LotoMuhanjan/
├── backend/          # FastAPI бэкенд
│   ├── app/
│   │   ├── api/     # Эндпоинты
│   │   ├── core/    # Конфигурация
│   │   ├── db/      # Модели и сессии БД
│   │   ├── schemas/ # Pydantic схемы
│   │   └── main.py  # Точка входа
│   ├── .env         # Переменные окружения
│   └── requirements.txt
│
├── frontend/         # Vue 3 фронтенд
│   ├── src/
│   │   ├── api/     # API клиенты
│   │   ├── composables/ # Хуки
│   │   ├── router/  # Роутинг
│   │   ├── views/   # Страницы
│   │   └── main.ts  # Точка входа
│   ├── vite.config.ts
│   └── package.json
│
├── bot/              # Telegram бот
│   ├── handlers/    # Обработчики
│   ├── keyboards/   # Клавиатуры
│   ├── main.py      # Точка входа
│   └── requirements.txt
│
└── README.md
```

---

## 🚀 Быстрый старт

### Требования

- Python 3.12+
- Node.js 18+
- PostgreSQL 14+
- Yarn или npm

### 1. Клонирование репозитория

```bash
git clone --recurse-submodules https://github.com/KazakhGamesLab/LotoMuhanjan.git
cd LotoMuhanjan
```

### 2. Настройка Backend

```bash
cd backend

# Создание виртуального окружения
python3 -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Установка зависимостей
pip install -r requirements.txt

# Настройка переменных окружения
cp .env.example .env
# Отредактируйте .env файл

# Создание базы данных
createdb loto

# Запуск сервера
uvicorn app.main:app --reload --host 0.0.0.0 --port 8092
```

Документация API будет доступна по адресу: `http://localhost:8092/docs`

### 3. Настройка Frontend

```bash
cd frontend

# Установка зависимостей
yarn install

# Настройка переменных окружения
cp .env.example .env
# Отредактируйте .env файл

# Запуск dev-сервера
yarn dev
```

Приложение будет доступно по адресу: `http://localhost:3000`

### 4. Настройка Bot

```bash
cd bot

# Создание виртуального окружения
python3 -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Установка зависимостей
pip install -r requirements.txt

# Настройка переменных окружения
cp .env.example .env
# Отредактируйте .env файл

# Запуск бота
python main.py
```

---

## 📋 Переменные окружения

### Backend (`.env`)

```env
DATABASE_URL=postgresql+asyncpg://user:password@localhost:5432/loto
CORS_ORIGINS=["https://yourdomain.com","http://localhost:3000"]
```

### Frontend (`.env`)

```env
VITE_API_URL=http://localhost:8092/api/v1
VITE_BOT_URL=https://t.me/your_bot_username
```

### Bot (`.env`)

```env
BOT_TOKEN=your_bot_token_here
WEBHOOK_URL=https://yourdomain.com/webhook
WEB_APP_URL=https://yourdomain.com/
```

---

## 🧪 Тестирование

### Backend

```bash
cd backend
pytest
```

### Frontend

```bash
cd frontend
yarn test
```

### Bot

```bash
cd bot
pytest
```

---

## 📚 API Документация

После запуска бэкенда доступна интерактивная документация:

- **Swagger UI**: `http://localhost:8092/docs`
- **ReDoc**: `http://localhost:8092/redoc`
- **OpenAPI JSON**: `http://localhost:8092/openapi.json`

---

## 🛠️ Технологии

### Бэкенд

- **FastAPI** — современный фреймворк для создания API
- **SQLAlchemy** — ORM для работы с базой данных
- **asyncpg** — асинхронный драйвер PostgreSQL
- **Pydantic** — валидация данных и типобезопасность

### Фронтенд

- **Vue 3** — прогрессивный фреймворк для создания интерфейсов
- **TypeScript** — типобезопасная разработка
- **Vite** — быстрый сборщик и dev-сервер
- **Vue Router** — маршрутизация приложения
- **@telegram-apps/sdk** — интеграция с Telegram Web Apps

### Бот

- **Aiogram 3.x** — асинхронная библиотека для создания ботов
- **Webhook** — обработка запросов от Telegram

### База данных

- **PostgreSQL** — надежная реляционная СУБД

---

## 🤝 Участие в проекте

Мы приветствуем вклад в развитие проекта! Вот как вы можете помочь:

1. 🐛 **Нашли баг?** — создайте issue
2. 💡 **Есть идея?** — предложите новую функцию
3. 🔧 **Хотите помочь?** — сделайте pull request

### Правила внесения изменений

1. Форкните репозиторий
2. Создайте ветку для вашей функции (`git checkout -b feature/amazing-feature`)
3. Сделайте коммит изменений (`git commit -m 'Add amazing feature'`)
4. Запушьте ветку (`git push origin feature/amazing-feature`)
5. Откройте Pull Request

---

## 📝 Лицензия

Этот проект распространяется под лицензией MIT. Подробнее см. в файле [LICENSE](LICENSE).

---

## 👥 Авторы

- **[KazakhGamesLab](https://github.com/KazakhGamesLab)** — основная команда разработки

---

## 🙏 Благодарности

- [FastAPI](https://fastapi.tiangolo.com/) — за прекрасный фреймворк
- [Vue.js](https://vuejs.org/) — за элегантный фронтенд-фреймворк
- [Aiogram](https://docs.aiogram.dev/) — за мощную библиотеку для ботов
- [Telegram](https://telegram.org/) — за платформу и инструменты разработки


