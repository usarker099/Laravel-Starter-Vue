 
# Laravel Starter - Vue - Boilerplate

A modern admin dashboard built with Laravel, Vue.js, Inertia, DaisyUI, and Spatie Permission for role-based access control. To Speed Up your project, Download and dive into Development.

## Features - Out Of box you are getting:

- User authentication and management
- User, Role and permission CRUD
- Responsive UI with DaisyUI components
- Inertia.js for seamless SPA navigation
- Protected routes with Spatie middleware
- All DaisyUI 35 theme Change Ability
- A simple SideBar and Navbar = Admin Dashboard.


## Tech Stack

- **Backend**: Laravel 11
- **Frontend**: Vue.js 3, Inertia.js
- **UI**: Tailwind CSS, DaisyUI
- **Auth & Permissions**: Spatie Laravel Permission, jetstream
- **Database**: MySQL/PostgreSQL

## Installation

1. Clone the repo:
   ```
   git clone https://github.com/usarker099/Laravel-Starter-Vue.git
   cd myapp
   ```

2. Install dependencies:
   ```
   composer install
   npm install
   ```

3. Set env: Set These according to your XAMP/MAMP/WAMP etc
```
   DB_CONNECTION=mysql
  DB_HOST=127.0.0.1
  DB_PORT=3306
  DB_DATABASE=abc
  DB_USERNAME=root
  DB_PASSWORD=
```

4. Generate key:
   ```
   php artisan key:generate
   ```

5. Setup database:
   ```
   php artisan migrate
   php artisan db:seed
   ```

6. Build assets:
   ```
   npm run dev
   ```
7. Import Project Database: Database file is included in project starter.sql
   ```
   - From Phpmyadmin navigate to database. Delete your migrated tables from DB_DATABASE=abc (or whatever name you give)
   - Then import starter.sql
   ```
8. Run server:
   ```
   php artisan serve
   ```

## Usage

- Access at `http://localhost:8000`. 
- Login with credentials:
UserName: admin@admin.com / 
password: password

## Contributing

Fork, branch, PR. Follow Laravel coding standards.

## License

MIT
