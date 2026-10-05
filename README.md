# Vue Laravel Auth Kit

A starter kit for authentication in Laravel 9 with a Vue 3 front end delivered through Inertia.js. It provides a complete browser-based sign-in flow and a token-based JSON API for mobile or single-page clients.

## Features

- Registration, login, logout, password reset and email verification (Laravel Breeze with Inertia and Vue)
- Profile page for updating account details and deleting the account
- Password confirmation for sensitive actions
- Token API with Laravel Sanctum:
  - `POST /api/signup` validates input and creates a user with a hashed password
  - `POST /api/login` returns a personal access token on success
  - `GET /api/user` returns the authenticated user (requires a bearer token)
- Tailwind CSS styling and Ziggy for named routes in JavaScript

## Tech Stack

| Area | Technology |
| --- | --- |
| Backend | PHP 8, Laravel 9, Laravel Sanctum |
| Frontend | Vue 3, Inertia.js, Tailwind CSS, Vite |
| Routing helper | Ziggy |
| Database | MySQL |
| Testing | PHPUnit |

## Project Structure

```text
laravel-vue-auth
├── app/Http/Controllers
│   ├── AuthController.php        Token signup and login
│   ├── ProfileController.php
│   └── Auth                      Breeze authentication controllers
├── resources/js
│   ├── Pages                     Welcome, Dashboard, Auth/*, Profile/*
│   ├── Components, Layouts
│   └── app.js
├── routes                        web.php, api.php, auth.php
├── database/migrations
└── tests
```

## Getting Started

### Prerequisites

- PHP 8.0.2 or later and Composer
- Node.js 16 or later
- MySQL

### Installation

```bash
git clone https://github.com/mosesaderemi/vue-laravel-auth-kit.git
cd vue-laravel-auth-kit/laravel-vue-auth
copy .env.example .env
composer install
php artisan key:generate
```

Set `DB_DATABASE`, `DB_USERNAME` and `DB_PASSWORD` in `.env`, create the database, then:

```bash
php artisan migrate
npm install
npm run dev
```

In a second terminal run `php artisan serve` and open `http://localhost:8000`.

### Email

Verification and reset emails use the SMTP settings in `.env`. For local testing point them to Mailpit or Mailtrap.

### API example

```bash
curl -X POST http://localhost:8000/api/signup \
  -H "Accept: application/json" -H "Content-Type: application/json" \
  -d '{"name":"Ada","email":"ada@example.com","password":"password123","password_confirmation":"password123"}'

curl -X POST http://localhost:8000/api/login \
  -H "Accept: application/json" -H "Content-Type: application/json" \
  -d '{"email":"ada@example.com","password":"password123"}'
```

Send the returned token as `Authorization: Bearer <token>` to reach protected routes.

## Testing

```bash
php artisan test
```

## Author

Aderemi Moses Timileyin
GitHub: [@mosesaderemi](https://github.com/mosesaderemi)
LinkedIn: [linkedin.com/in/mosesaderemi-6a70a5405](https://www.linkedin.com/in/mosesaderemi-6a70a5405)

## License

Released under the MIT License. See the `LICENSE` file for details.
