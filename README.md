# Setting up NGINXpHP on Windows

This guide will walk you through the steps to set up NGINX and PHP on your Windows machine for web development. This setup will allow you to run web applications locally using NGINX as the web server and PHP for server-side scripting.

## Setting up NGINX

1. **Download NGINX for Windows:**

   Download the latest version of NGINX for Windows from the [official NGINX website](https://nginx.org/).

2. **Create NGINX Directory:**

   - Go to the `C:/` directory on your machine.
   - Create a new folder named `C:/nginx`.

3. **Unzip NGINX:**

   - Unzip the downloaded NGINX .zip file into the `C:/nginx` directory.

4. **Create NGINX Configuration Folders:**

   - Inside the `C:/nginx` directory, create two new folders named `sites-available` and `sites-enabled`.

5. **Test NGINX:**

   - To test if NGINX is working, double-click on `C:/nginx/nginx.exe`.
   - Open your web browser and type `localhost`. You should see the NGINX welcome page.
   - To stop NGINX, use the Task Manager to kill the NGINX process.

## Setting up PHP

1. **Download PHP for Windows:**

   Download the PHP version of your choice (e.g., PHP 8.1) for Windows from the [official PHP website](https://windows.php.net/download/).

2. **Create PHP Directory:**

   - Go to the `C:/` directory on your machine.
   - Create a new folder named `C:/php` (or a version-specific folder like `C:/php8.1`).

3. **Unzip PHP:**

   - Unzip the downloaded PHP .zip file into the `C:/php` directory.

4. **Add PHP to Environment Variables:**

   - Add the path `C:/php` (or your PHP version folder) to your system's environment variables.

5. **Verify PHP Installation:**

   - Open Command Prompt and type `php -v`. You should see the PHP version information if it's installed correctly.

## Running NGINX and PHP as Services

To run NGINX and PHP as background services, follow these steps:

1. **Install NSSM Service Manager:**

   - Download and unzip NSSM Service Manager from [here](https://nssm.cc/download).

2. **Install NGINX as a Service:**

   - Open Command Prompt as an Administrator.
   - Navigate to the `C:/nssm/win64/` directory.
   - Run `nssm install nginx`.
   - Define the path of the `nginx.exe` file.
   - Click "Install Service."
   - Start the NGINX service from the Windows Services Manager.

3. **Install PHP as a Service:**

   - Open Command Prompt as an Administrator.
   - Navigate to the `C:/nssm/win64/` directory.
   - Run `nssm install php`.
   - Define the path of the `php-cgi.exe` file.
   - Add the arguments: `-b 127.0.0.1:9000`.
   - Click "Install Service."
   - Start the PHP service from the Windows Services Manager.

## Testing Your Setup

1. **Configure NGINX Sites:**

   - Create NGINX configuration files for your websites inside the `C:/nginx/sites-available` directory.
   - Enable your site by creating symlinks in the `C:/nginx/sites-enabled` directory.

2. **Test Your Configuration:**

   - Run `nginx -t` in the `C:/nginx` directory to ensure there are no configuration errors.

3. **Add Host Entries:**

   - Edit your hosts file (`C:\Windows\System32\drivers\etc\hosts`) and add entries like `127.0.0.1 example.com` for your configured sites.

4. **Access Your Sites:**

   - Open your web browser and access your configured sites by name (e.g., `http://example.com`).

5. **Troubleshooting:**

   - If you encounter "Connection Refused" errors, check your firewall settings and ensure the PHP service is running.

Happy web development with NGINX and PHP on Windows!
