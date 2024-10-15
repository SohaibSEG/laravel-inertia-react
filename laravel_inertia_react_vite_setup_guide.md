
# Setup Guide: Laravel + Inertia.js + React + Vite + MySQL

## 1. Installation Instructions

### Windows

1. **Install PHP**:
   - Download PHP from [php.net](https://www.php.net/downloads) and follow the Windows installation guide.
   - Add PHP to your system `PATH` during installation.

2. **Install Composer**:
   - Download and install Composer from [getcomposer.org](https://getcomposer.org/download/).
   - Verify installation:
     ```bash
     composer -V
     ```

3. **Install Node.js and npm**:
   - Download Node.js from [nodejs.org](https://nodejs.org/). Install the LTS version.
   - Verify installation:
     ```bash
     node -v
     npm -v
     ```

4. **Install MySQL**:
   - Download MySQL from [mysql.com](https://dev.mysql.com/downloads/installer/).
   - Set up a root password and create a new database:
     ```sql
     CREATE DATABASE my_database;
     ```

---

### Linux (Ubuntu/Debian)

1. **Install PHP**:
   ```bash
   sudo apt update
   sudo apt install php php-cli php-mbstring php-xml php-zip php-mysql
   ```

2. **Install Composer**:
   ```bash
   curl -sS https://getcomposer.org/installer | php
   sudo mv composer.phar /usr/local/bin/composer
   ```

3. **Install Node.js and npm**:
   ```bash
   sudo apt install nodejs npm
   ```

   Verify installation:
   ```bash
   node -v
   npm -v
   ```

4. **Install MySQL**:
   ```bash
   sudo apt install mysql-server
   sudo mysql_secure_installation
   ```

   Create a new database:
   ```sql
   CREATE DATABASE my_database;
   ```

---

## 2. Laravel + Inertia.js + React + Vite Configuration

The configuration and setup steps from here on are **the same** for both Windows and Linux.

### Step 1: Create a New Laravel Project

1. Open your terminal/command prompt and run the following to create a new Laravel project:

   ```bash
   composer create-project laravel/laravel my-laravel-app
   ```

2. Navigate into the project directory:

   ```bash
   cd my-laravel-app
   ```

### Step 2: Set Up MySQL Database

1. Open the `.env` file in the project directory and update the database connection details to match your MySQL credentials:

   ```bash
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=my_database
   DB_USERNAME=root
   DB_PASSWORD=your_password
   ```

2. Run Laravel migrations to create the necessary database tables:

   ```bash
   php artisan migrate
   ```

### Step 3: Install Inertia.js, React, and Vite

1. **Install Inertia.js**:

   ```bash
   composer require inertiajs/inertia-laravel
   ```

2. **Install React, Vite, and other dependencies**:

   ```bash
   npm install @inertiajs/inertia @inertiajs/inertia-react @inertiajs/progress react react-dom
   ```

3. **Install Vite (Laravel 9+ uses Vite by default)**:

   ```bash
   npm install
   ```

### Step 4: Configure Vite

1. Open the `vite.config.js` file and configure Vite to work with Laravel and React:

   ```javascript
   import { defineConfig } from 'vite';
   import react from '@vitejs/plugin-react';
   import { resolve } from 'path';

   export default defineConfig({
     plugins: [react()],
     resolve: {
       alias: {
         '@': resolve(__dirname, 'resources/js'),
       },
     },
     server: {
       hmr: {
         host: 'localhost',
       },
     },
   });
   ```

### Step 5: Set Up Inertia.js with React

1. Set up Inertia.js and React in `resources/js/app.js`:

   ```javascript
   import { createInertiaApp } from '@inertiajs/inertia-react';
   import { InertiaProgress } from '@inertiajs/progress';
   import { render } from 'react-dom';

   createInertiaApp({
       resolve: name => require(`./Pages/\${name}`).default,
       setup({ el, App, props }) {
           render(<App {...props} />, el);
       },
   });

   InertiaProgress.init();
   ```

2. Define your routes in `routes/web.php` to render React components via Inertia:

   ```php
   use Inertia\Inertia;

   Route::get('/', function () {
       return Inertia::render('Home');
   });
   ```

3. Create a simple `Home.jsx` React component in `resources/js/Pages/Home.jsx`:

   ```javascript
   const Home = () => {
       return (
           <div>
               <h1>Welcome to Inertia.js with React!</h1>
           </div>
       );
   }

   export default Home;
   ```

### Step 6: Compile Assets and Run the Application

1. **Run Vite** for hot module replacement (HMR) during development:

   ```bash
   npm run dev
   ```

2. **Serve the Laravel application**:

   ```bash
   php artisan serve
   ```

Now, navigate to `http://127.0.0.1:8000` in your browser, and you’ll see your Laravel app running with Inertia.js, React, and Vite!

---

## Node.js Ecosystem Overview

- **Node.js**: JavaScript runtime for running server-side code.
- **npm**: Node package manager that installs JavaScript libraries.
- **Vite**: Fast build tool and development server used to compile and bundle React components.

With this setup, you can now develop a full-stack SPA using **Laravel** for the backend and **React** with **Inertia.js** for the frontend in a single project!
