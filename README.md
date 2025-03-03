# Lumen Laravel API

Lumen is a lightweight PHP framework built by Laravel for microservices and APIs. This guide provides a step-by-step setup for Lumen.

## Installation

### 1. Install Lumen
```sh
composer create-project --prefer-dist laravel/lumen my-lumen-app
cd my-lumen-app
```

### 2. Enable Eloquent & Facades
Modify `bootstrap/app.php`:
```php
$app->withFacades();
$app->withEloquent();
```

### 3. Configure Environment Variables
Rename `.env.example` to `.env` and configure your database:
```ini
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=lumen_db
DB_USERNAME=root
DB_PASSWORD=
```

## Routing
Define routes in `routes/web.php` or `routes/api.php`:

### GET Request Example
```php
$router->get('/users', function () {
    return response()->json(['message' => 'GET request successful']);
});
```

### POST Request Example
```php
$router->post('/users', function (\Illuminate\Http\Request $request) {
    return response()->json(['message' => 'POST request successful', 'data' => $request->all()]);
});
```

## Running the Server
Start the local development server:
```sh
php -S localhost:8000 -t public
```

## Testing API Requests
Use **Postman** or **cURL** to test:
```sh
curl -X GET http://localhost:8000/users
curl -X POST -d "name=John" http://localhost:8000/users
```

## Database Migrations
Create a migration:
```sh
php artisan make:migration create_users_table
```
Run migrations:
```sh
php artisan migrate
```
