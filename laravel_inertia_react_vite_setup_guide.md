
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

alternatively you can install XAMPP/WAMP
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

### Step 3: Install Breeze with Inertia, react and vite

1. **Install laravel/breeze**:
   
   ```bash
   composer require larvel/breeze --dev
   ```

2. **Install React, Vite, and other dependencies using breeze**:

   ```bash
   php artisan breeze:install
   # select react
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

