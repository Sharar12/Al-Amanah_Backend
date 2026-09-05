# Al-Amanah — Backend

The backend API for the **Al-Amanah** financial management application. It is a Laravel 12 application using PHP 8.2+, Laravel Sanctum authentication, relational database migrations, role-based authorization, and REST-style API endpoints for the frontend application.

## Overview

This repository contains the server-side application responsible for authentication, authorization, financial data, transaction processing, receipts, reports, expenses, FDR records, notifications, user/member administration, settings, profile sharing, and activity logs.

The backend is designed to serve the separate **Al-Amanah Frontend** application.

## Tech Stack

| Technology | Purpose |
| --- | --- |
| Laravel 12 | Backend framework and HTTP/API layer |
| PHP 8.2+ | Server-side runtime |
| Laravel Sanctum 4 | Token-based API authentication |
| Eloquent ORM | Database access and relationships |
| MySQL / relational database | Application persistence |
| PHPUnit | Automated testing |
| Laravel Pint | PHP code style |
| Laravel Pail | Local application logging |

The project requires PHP `^8.2`, Laravel `^12.0`, and Laravel Sanctum `^4.0`. fileciteturn72file0

## Core Capabilities

### Authentication & Authorization

- Login, logout, and authenticated-user endpoints.
- Laravel Sanctum bearer-token authentication.
- Role-based access control for `super_admin`, `admin`, and `accountant` workflows.
- Payment-permission middleware for sensitive financial operations.
- Server-side authorization remains the final security boundary.

### Financial Management

- Transactions and payment demands.
- Full and partial payment collection.
- Receipt and receipt-photo workflows.
- Batch receipt-photo processing.
- Transaction reporting and dashboard statistics.
- Meeting expenses.
- FDR records.
- Notifications.

### Administration

- User/member management.
- Role and permission management.
- Admin payment permissions.
- Application settings.
- Activity logs.
- Profile shares / linked accounts.

## API Areas

The API routes currently cover:

```text
Authentication
├── /api/login
├── /api/logout
└── /api/me

Users / Roles / Permissions
├── /api/users
├── /api/roles
├── /api/permissions
└── /api/admin-payment-permissions

Transactions / Payments
├── /api/transactions
├── /api/transactions/generate-payments
├── /api/transactions/{id}/collect-payment
├── /api/transactions/{id}/upload-receipt-photo
└── /api/transactions/batch-upload-receipt-photo

Receipts / Reports / Expenses / FDR
├── /api/receipts
├── /api/reports/transactions
├── /api/reports/stats
├── /api/meeting-expenses
└── /api/fdrs

Other
├── /api/notifications
├── /api/settings
├── /api/profile-shares
├── /api/activity-logs
└── /api/id-photos/{filename}
```

Sensitive endpoints are grouped behind Sanctum authentication and role/permission middleware in `routes/api.php`. fileciteturn76file0

## Project Structure

```text
Al-Amanah_Backend/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   ├── Middleware/
│   │   └── Requests/
│   ├── Models/
│   └── Providers/
│
├── bootstrap/
├── config/
├── database/
│   ├── factories/
│   ├── migrations/
│   └── seeders/
├── public/
├── resources/
├── routes/
│   └── api.php
├── storage/
├── tests/
├── artisan
├── composer.json
├── .env.example
└── README.md
```

## Environment Configuration

Create your local environment file from `.env.example`:

```bash
cp .env.example .env
```

Configure the application key, database connection, URL, Sanctum-related settings, and any other services required by the environment.

Never commit a populated `.env` file or production credentials.

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Sharar12/Al-Amanah_Backend.git
cd Al-Amanah_Backend
```

### 2. Install PHP dependencies

```bash
composer install
```

### 3. Configure environment

```bash
cp .env.example .env
php artisan key:generate
```

### 4. Configure the database

Update the database variables in `.env`, then run:

```bash
php artisan migrate
```

### 5. Start the API server

```bash
php artisan serve
```

The local API is normally available at:

```text
http://127.0.0.1:8000
```

## Useful Commands

```bash
php artisan serve            # Start the Laravel server
php artisan migrate          # Run database migrations
php artisan migrate:fresh    # Recreate the database from migrations
php artisan db:seed          # Run database seeders
php artisan route:list       # Inspect registered routes
php artisan optimize:clear   # Clear cached configuration/routes/views
php artisan test             # Run the test suite
./vendor/bin/pint            # Format PHP code with Laravel Pint
```

The Composer configuration also provides `composer test` and a combined `composer dev` workflow for local development. fileciteturn72file0

## Frontend Integration

Frontend repository:

```text
https://github.com/Sharar12/Al-Amanah_Frontend
```

The frontend consumes the API under the `/api` prefix and sends Sanctum bearer tokens for authenticated requests.

## Security Notes

- Keep secrets in environment variables, not source control.
- Use HTTPS for production API traffic.
- Keep authorization checks on the backend even when the frontend already hides protected UI.
- Protect private files and sensitive financial data with authenticated, authorized endpoints.
- Review database backups and any exported data before sharing or publishing them.

## License

This project is licensed under the license included in the repository.
