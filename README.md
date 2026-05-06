Here’s your **fully structured, clean, beginner-friendly README** with the **“new system Laravel installation”** properly included and everything flowing logically (no duplication, no confusion).

---

# Laravel Project Setup Guide

A complete step-by-step guide to installing Laravel on a new system, creating a project, and pushing it to GitHub.

---

## Requirements

Make sure your system has:

* PHP 8.2 or higher
* Composer
* Node.js and npm
* Git

---

## 1. Install Laravel (For a New System)

If Laravel is not set up on your machine yet, follow these steps.

### 1.1 Install Composer

Check if Composer is installed:

```bash
composer --version
```

If not, install it from: [https://getcomposer.org](https://getcomposer.org)

---

### 1.2 Install Laravel Installer (Optional)

```bash
composer global require laravel/installer
```

---

### 1.3 Add Composer to PATH

#### Linux / macOS

```bash
export PATH="$HOME/.config/composer/vendor/bin:$PATH"
```

#### Windows

Add this path to Environment Variables:

```
C:\Users\YourUsername\AppData\Roaming\Composer\vendor\bin
```

---

### 1.4 Verify Laravel Installation

```bash
laravel --version
```

---

## 2. Create a Laravel Project

### Option A — Using Laravel Installer

```bash
laravel new my-laravel-app
cd my-laravel-app
```

### Option B — Using Composer (Recommended)

```bash
composer create-project laravel/laravel my-laravel-app
cd my-laravel-app
```

---

## 3. Create a GitHub Repository

1. Go to [https://github.com](https://github.com)
2. Click **New repository**
3. Name it (e.g. `my-laravel-app`)
4. Leave it empty (no README, no .gitignore)
5. Click **Create repository**

---

## 4. Connect Project to GitHub

```bash
git init
git remote add origin https://github.com/your-username/your-repo-name.git
```

---

## 5. Configure Environment

```bash
cp .env.example .env
php artisan key:generate
```

Update `.env`:

```env
APP_NAME=YourAppName
APP_URL=http://localhost

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=your_database_name
DB_USERNAME=root
DB_PASSWORD=
```

---

## 6. Run Migrations

```bash
php artisan migrate
```

---

## 7. Install Frontend Dependencies

```bash
npm install
npm run dev
```

---

## 8. Start Development Server

```bash
php artisan serve
```

Visit:

```
http://127.0.0.1:8000
```

---

## 9. Push to GitHub

### Generate Personal Access Token (PAT)

1. GitHub → Settings
2. Developer settings → Personal access tokens
3. Generate new token (classic)
4. Select **repo**
5. Copy token

---

### Push Code

```bash
git add .
git commit -m "Initial Laravel setup"
git branch -M main
git push -u origin main
```

---

## 10. Clone on a New Machine

```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
composer install
cp .env.example .env
php artisan key:generate
```

Then:

```bash
php artisan migrate
npm install
npm run dev
php artisan serve
```

---

## What is NOT Pushed to GitHub

Laravel automatically ignores:

| Item            | Reason                 |
| --------------- | ---------------------- |
| `.env`          | Contains secrets       |
| `/vendor`       | Installed via Composer |
| `/node_modules` | Installed via npm      |
| `/storage`      | Logs and cache         |

---

## Useful Artisan Commands

```bash
php artisan serve
php artisan key:generate
php artisan migrate
php artisan migrate:rollback
php artisan make:controller PostController
php artisan make:model Post -m
php artisan route:list
php artisan tinker
```

---

## Open in VS Code

```bash
code .
```

---
