# BoxManager — Система управления коробками

## Структура проекта

```
├── DB/
│   └── database.sql        — SQL-скрипт БД (схема + тестовые данные)
├── Documents/
│   └── Documents.docx      — Пояснительная записка
└── Source/
    ├── backend/             — NestJS сервер (порт 3000)
    └── frontend/            — React приложение (порт 3001)
```

## Запуск проекта

### 1. База данных (PostgreSQL + DBeaver)
1. Открыть DBeaver, подключиться к PostgreSQL (localhost:5432)
2. Создать БД: `CREATE DATABASE box_management;`
3. Открыть файл `DB/database.sql` и выполнить его

### 2. Backend (NestJS)
```bash
cd Source/backend
npm install
# Настроить .env (или оставить значения по умолчанию)
npm run start:dev
# Сервер запустится на http://localhost:3000
```

### 3. Frontend (React)
```bash
cd Source/frontend
npm install
npm start
# Приложение откроется на http://localhost:3001
```

## API Endpoints

| Метод  | URL                        | Описание                        | Доступ      |
|--------|----------------------------|---------------------------------|-------------|
| POST   | /api/auth/login            | Вход в систему                  | Все         |
| GET    | /api/auth/me               | Текущий пользователь            | JWT         |
| GET    | /api/users                 | Список пользователей            | admin/mngr  |
| GET    | /api/users/:id             | Пользователь по id              | JWT         |
| POST   | /api/users                 | Создать пользователя            | Все         |
| PUT    | /api/users/:id             | Обновить пользователя           | admin       |
| DELETE | /api/users/:id             | Удалить пользователя            | admin       |
| GET    | /api/boxes                 | Список коробок                  | Все         |
| GET    | /api/boxes/:id             | Коробка по id                   | Все         |
| POST   | /api/boxes                 | Создать коробку                 | admin/mngr  |
| PUT    | /api/boxes/:id             | Обновить коробку                | admin/mngr  |
| DELETE | /api/boxes/:id             | Удалить коробку                 | admin       |
| GET    | /api/categories            | Список категорий                | Все         |
| POST   | /api/categories            | Создать категорию               | admin/mngr  |
| PUT    | /api/categories/:id        | Обновить категорию              | admin/mngr  |
| DELETE | /api/categories/:id        | Удалить категорию               | admin       |
| GET    | /api/orders                | Все заказы                      | admin/mngr  |
| GET    | /api/orders/my             | Мои заказы                      | JWT         |
| POST   | /api/orders                | Создать заказ                   | JWT         |
| PATCH  | /api/orders/:id/status     | Изменить статус заказа          | JWT         |
| DELETE | /api/orders/:id            | Удалить заказ                   | admin       |

## Тестовые учётные данные
После запуска базы данных создайте пользователя через POST /api/users или через форму регистрации.

Роли: admin, manager, user
