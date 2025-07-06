Laravel 12 Full Tutorial - Project Setup & Guide
Laravel 12 Full Tutorial - Project Setup & Guide
A complete Laravel 12 application guide with user authentication, database interaction, admin/user roles, routing, API support, and frontend integration (Blade + optional Vite + Tailwind/Bootstrap).
---
📁 Project Overview
This Laravel 12 project includes:
•	- ✅ Laravel Breeze Authentication (Login/Register)
•	- 🔐 Role-Based Access Control (Admin/User)
•	- 📦 RESTful API Setup with Sanctum
•	- 📄 Blade Templating
•	- 🎨 Tailwind CSS (via Vite)
•	- 📚 CRUD Operations
•	- 🌐 Routing and Middleware
•	- 🧪 Form Validation
•	- 🧰 Artisan Commands
•	- 🗃️ Migration & Seeder
•	- 🧪 Unit & Feature Tests
---
🚀 Installation Guide
🛠️ Requirements
•	- PHP >= 8.2
•	- Composer
•	- MySQL / PostgreSQL / SQLite
•	- Node.js & NPM (for frontend assets)
📥 Clone the Repository

git clone branch-name
cd laravel12-project

📦 Install PHP Dependencies

composer install

🗄️ Environment Setup

cp .env.example .env
php artisan key:generate

Edit `.env` and set your database credentials:

DB_DATABASE=your_db
DB_USERNAME=root
DB_PASSWORD=secret

🧬 Run Migrations & Seeders

php artisan migrate --seed

📝 Seeders will create default Admin/User accounts.
🌐 Run Dev Server

php artisan serve

---
🎨 Frontend (Vite & TailwindCSS)
Install NPM Packages

npm install

Start Development Server

npm run dev

Make sure your `vite.config.js` is properly configured for Laravel.
---
🔐 Authentication
This project uses **Laravel Breeze** for simple auth.

composer require laravel/breeze --dev
php artisan breeze:install
npm install && npm run dev
php artisan migrate

---
🧭 Routing
Routes are defined in:
•	- `routes/web.php` - Web Interface
•	- `routes/api.php` - REST API
Example Route:

Route::get('/dashboard', [DashboardController::class, 'index'])->middleware('auth');

---
🧩 Controllers & Views
Generate a controller:

php artisan make:controller UserController

Blade views are stored in `resources/views`.
Example: `resources/views/user/dashboard.blade.php`
---
🧾 CRUD Example
Create Model, Migration, and Controller:

php artisan make:model Product -mcr

Run migration:

php artisan migrate

---
🧪 Validation
Example inside Controller:

$request->validate([
'name' => 'required|string|max:255',
'price' => 'required|numeric',
]);

---
🧑💼 Admin vs User Roles (RBAC)
In UserSeeder or Registration logic:

$user->role = 'admin'; // or 'user'

Use Middleware:

public function handle($request, Closure $next)
{
if (auth()->user()->role !== 'admin') {
abort(403);
}
return $next($request);
}

Register middleware in `app/Http/Kernel.php`.
---
🛠️ Artisan Useful Commands

php artisan list
php artisan make:model Post -mcr
php artisan migrate:fresh --seed
php artisan route:list

---
🔐 Sanctum API Auth (Optional)

composer require laravel/sanctum
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
php artisan migrate

Use `auth:sanctum` middleware in `api.php`.
---
📬 API Example (Optional)
GET

GET /api/products
Authorization: Bearer <token>

POST

POST /api/products
{
"name": "Laptop",
"price": 50000
}

---
🧪 Testing (Optional)

php artisan make:test ProductTest
php artisan test

---
📁 Folder Structure (Key Folders)
•	- `app/Http/Controllers` — Business logic
•	- `app/Models` — Eloquent models
•	- `resources/views` — Blade templates
•	- `routes/` — Routing files
•	- `public/` — Public assets
•	- `database/migrations` — Schema changes
•	- `database/seeders` — Test data
•	- `tests/` — Automated tests
---
💬 Contribution
1. Fork this repo
2. Create your feature branch (`git checkout -b feature/feature-name`)
3. Commit your changes
4. Push to the branch
5. Open a Pull Request
---
## 🧑‍💻 Maintainer
👤 **Sambit Pattanaik**
---
📄 License
This project is open-source and available under the [MIT License](LICENSE).
