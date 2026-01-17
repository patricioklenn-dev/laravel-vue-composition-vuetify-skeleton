# Laravel Vue Skeleton

Laravel Vue Skeleton es una aplicación base con Laravel 12, Vue 3.5 (Composition API), Inertia.js y Vuetify 3. Incluye autenticación (login, registro, recuperación de contraseña, verificación de email) y gestión de perfil de usuario. Utiliza Vite 5 como herramienta de build y está configurado para desarrollo con soporte en español.

## Stack

- **Backend**: Laravel 12 (PHP 8.2+)
- **Frontend**: Vue.js 3.5 (Composition API) with Inertia.js
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
