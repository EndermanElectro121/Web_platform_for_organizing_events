1. Архітектура

EventHub має клієнт-серверну архітектуру: Angular відповідає за інтерфейс користувача, Node.js та Express — за серверну логіку, Prisma — за роботу з базою даних PostgreSQL.

Схема роботи:

Angular Front-end
        ↓
REST API
        ↓
Node.js + Express
        ↓
Prisma ORM
        ↓
PostgreSQL


2. Основні API

Метод    URL                              Дія
---------------------------------------------------------------------------
POST     /api/auth/register              Реєстрація
POST     /api/auth/login                 Вхід
GET      /api/events/public              Афіша
GET      /api/events                     Події користувача
POST     /api/events                     Створення події
PUT      /api/events/:id                 Редагування
DELETE   /api/events/:id                 Видалення
PATCH    /api/events/:id/publish         Публікація
POST     /api/events/:id/register        Реєстрація на подію
GET      /api/events/:id/participants    Учасники
POST     /api/events/:id/reviews         Додати відгук


Для захищених запитів використовується JWT-токен:

Authorization: Bearer TOKEN


3. Запуск проєкту

1. Встановити Node.js і PostgreSQL.

2. Встановити залежності командою:

npm install

3. Створити файл .env та вказати необхідні змінні середовища:

DATABASE_URL=...
JWT_SECRET=...
PORT=3000

4. Виконати генерацію Prisma Client:

npx prisma generate

5. Виконати міграцію бази даних:

npx prisma migrate dev

6. Запустити back-end:

npm run dev

7. Запустити Angular:

npm start


Після запуску:

Front-end:
http://localhost:4200

Back-end:
http://localhost:3000

Основні зміни, які були внесені у цю версію: адаптивність застосунку під усы дозволи екрану, два пункта верхнєго меню: Події та Афіша без пункта Календарі та прибирання зайвих едементів.
