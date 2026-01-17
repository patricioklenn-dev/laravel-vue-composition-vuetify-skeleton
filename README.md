# Laravel Vue Skeleton

Laravel skeleton application with Vue.js, Inertia.js and Vuetify.

## Stack

- **Backend**: Laravel 12 (PHP 8.2+)
- **Frontend**: Vue.js 3 with Inertia.js
- **UI Framework**: Vuetify 3
- **Build Tool**: Vite 5
- **Testing**: Pest 3 with PHPUnit 11

## Features

- Authentication system (login, register, password reset, email verification)
- User profile management
- Modern UI with Vuetify components
- Spanish language support for validation messages

## Requirements

- PHP 8.2 or higher
- Composer
- Node.js 18+ and npm

## Installation

1. Clone the repository
2. Install PHP dependencies: `composer install`
3. Install Node dependencies: `npm install`
4. Copy `.env.example` to `.env` and configure your database
5. Generate application key: `php artisan key:generate`
6. Run migrations: `php artisan migrate`
7. Build assets: `npm run dev` or `npm run build`

## Development

Run the development server with all services (server, queue, and Vite):

```bash
composer dev
```

Or run services individually:

```bash
# Laravel development server
php artisan serve

# Vite dev server
npm run dev

# Queue worker
php artisan queue:listen
```

## Testing

Run tests using Pest:

```bash
php artisan test
# or
./vendor/bin/pest
```

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
