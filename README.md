# Laravel Project Setup Guide

A step-by-step guide to setting up a Laravel project and pushing it to GitHub.

---

## Requirements

Make sure you have the following installed before starting:

- PHP 8.2 or higher
- Composer
- Node.js and npm
- Git

---

## 1. Create a GitHub Repository

1. Go to [github.com](https://github.com) and log in
2. Click **New repository**
3. Give it a name (e.g. `my-laravel-app`)
4. Leave it completely empty — no README, no .gitignore
5. Click **Create repository**

---

## 2. Clone the Empty Repository

```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```

---

## 3. Install Laravel into the Current Folder

The `.` at the end installs Laravel directly into the repo folder instead of creating a subfolder.

```bash
composer create-project laravel/laravel .
```

> If Composer complains the folder is not empty, install into a temp folder and move the files:
> ```bash
> cd ..
> composer create-project laravel/laravel temp-laravel
> cp -r temp-laravel/. your-repo-name/
> rm -rf temp-laravel
> cd your-repo-name
> ```

---

## 4. Configure Environment

```bash
cp .env.example .env
php artisan key:generate
```

Open `.env` and update your app and database settings:

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

## 5. Run Migrations

Make sure your database exists, then run:

```bash
php artisan migrate
```

---

## 6. Install Frontend Dependencies

```bash
npm install
npm run dev
```

---

## 7. Start the Development Server

```bash
php artisan serve
```

Visit `http://127.0.0.1:8000` in your browser.

---

## 8. Push to GitHub

### Generate a Personal Access Token (PAT)

GitHub no longer accepts passwords over HTTPS. You need a token:

1. Go to GitHub → Profile photo → **Settings**
2. Scroll to **Developer settings** → **Personal access tokens → Tokens (classic)**
3. Click **Generate new token (classic)**
4. Check the **repo** scope and set an expiration
5. Click **Generate token** and copy it immediately

### Set the Remote URL with Your Token

```bash
git remote set-url origin https://YOUR_TOKEN@github.com/your-username/your-repo-name.git
```

### Commit and Push

```bash
git add .
git commit -m "Initial Laravel setup"
git push origin main
```

---

## 9. Cloning on a New Machine

When setting up the project on a different computer:

```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
composer install
cp .env.example .env
php artisan key:generate
```

Update `.env` with the new machine's database settings, then:

```bash
php artisan migrate
npm install
npm run dev
php artisan serve
```

---

## What is Not Pushed to GitHub

Laravel's `.gitignore` automatically excludes these — do not push them manually:

| Item | Reason |
|---|---|
| `.env` | Contains passwords and secret keys |
| `/vendor` | Composer reinstalls this via `composer install` |
| `/node_modules` | npm reinstalls this via `npm install` |
| `/storage` | Runtime files, logs, and cache |

---

## Quick Reference — Artisan Commands

```bash
php artisan serve                        # Start local server
php artisan key:generate                 # Generate app key
php artisan migrate                      # Run database migrations
php artisan migrate:rollback             # Undo last migration
php artisan make:controller PostController
php artisan make:model Post -m           # Model + migration
php artisan route:list                   # See all registered routes
php artisan tinker                       # Interactive shell
```

---

## Open in VS Code

To open the project folder in VS Code from the terminal:

```bash
code .
```