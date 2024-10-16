
# Setting up Laragon, PHP, Node.js, Composer, and MySQL on Windows with Laravel, Breeze, and Inertia (React)

## 1. Install Laragon

### Step 1: Download Laragon
- Visit [https://laragon.org/](https://laragon.org/) and download the full version of Laragon.

### Step 2: Install Laragon
- Run the installer and follow the instructions to install Laragon.
- Open Laragon after installation.

## 2. Add PHP, Node.js, Composer, and MySQL to the Windows Path

Laragon comes with PHP, Node.js, Composer, and MySQL pre-installed, but we need to ensure they are available in the system's environment variables (PATH).


### Step 2: Find Paths
Click menu > tools > path > manage path
To add PHP, Node.js, Composer, and MySQL to the Windows Path, you need their installation paths. These are typically located inside the Laragon directory:
- PHP: `C:\laragon\bin\php\php-[version]`
- Node.js: `C:\laragon\bin\nodejs`
- Composer: `C:\laragon\bin\composer`
- MySQL: `C:\laragon\bin\mysql\mysql-[version]`

### Step 3: Add Paths to Environment Variables
1. Open **Control Panel** > **System** > **Advanced System Settings**.
2. Click on the **Environment Variables** button.
3. Under **System variables**, scroll and find **Path**, then click **Edit**.
4. Add new entries for PHP, Node.js, Composer, and MySQL:
    - Add: `C:\laragon\bin\php\php-version`
    - Add: `C:\laragon\bin\nodejs`
    - Add: `C:\laragon\bin\composer`
    - Add: `C:\laragon\bin\mysql\mysql-version`
5. Save changes.

### Step 4: Verify Paths
- Open a new terminal (Command Prompt or PowerShell) and run the following commands to check if they are correctly installed:
    ```bash
    php -v
    node -v
    composer -v
    mysql --version
    ```

## 3. Create a New Laravel Application

### Step 1: Create a Laravel Project
- Run the following command to create a new Laravel project:
    ```bash
    composer create-project --prefer-dist laravel/laravel your-laravel-app
    ```

### Step 2: Navigate to Your Laravel Application Directory
- Navigate to your Laravel project directory:
    ```bash
    cd your-laravel-app
    ```

### Step 3: Install Breeze
- Install Laravel Breeze:
    ```bash
    composer require laravel/breeze --dev
    ```

- Run the Breeze installation command for Inertia with React:
    ```bash
    php artisan breeze:install react
    ```

### Step 4: Install Node Dependencies and Compile Assets
- Install Node.js dependencies and compile your assets:
    ```bash
    npm install
    npm run dev
    ```

### Step 5: Migrate the Database
- Run migrations to set up the database tables:
    ```bash
    php artisan migrate
    ```

### Step 6: Serve Your Application
- Run the following command to serve your Laravel application:
    ```bash
    php artisan serve
    ```

Your Laravel application with Breeze and Inertia (React) should now be up and running!

## 4. Access Your Application
- Open your browser and go to `http://localhost:8000` to view the Laravel application.
