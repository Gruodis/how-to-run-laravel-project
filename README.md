<p align="center"><img alt="Shows an illustrated sun in light mode and a moon with stars in dark mode." src="https://laravel.com/img/logomark.min.svg"></p>
<h1 align="center">
# Hot To Start Laravel Project
</h1>

# Start from scratch
- install composer [open setup link](https://www.digitalocean.com/community/tutorials/how-to-install-composer-on-ubuntu-22-04-quickstart). or follow these steps"
  - ## Step 1 — Install Dependencies
```bash
sudo apt update
sudo apt install php-cli unzip
```
## Step 2 — Download and Install Composer
#### Make sure you’re in your home directory, then retrieve the Composer installer using curl:
```bash
cd ~
curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
```
#### Using curl, fetch the latest signature and store it in a shell variable:
```bash
HASH=`curl -sS https://composer.github.io/installer.sig`
```
#### Now execute the following PHP code to verify that the installation script is safe to run:
```bash
php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
```
#### You’ll see the following output:
```bash
Installer verified
```
> **Note:**
_If the output says Installer corrupt, you’ll need to repeat the download and verification process until you have a verified installer._

#### The following command will download and install Composer as a system-wide command named **composer**, under **/usr/local/bin**:
```bash
sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```
#### You’ll see output similar to this:
```bash
Output
All settings correct for using Composer
Downloading...

Composer (version 2.3.5) successfully installed to: /usr/local/bin/composer
Use it: php /usr/local/bin/composer
```
### To test your installation, run:
```bash
composer
```
### Output:
```bash
Output
   ______
  / ____/___  ____ ___  ____  ____  ________  _____
 / /   / __ \/ __ `__ \/ __ \/ __ \/ ___/ _ \/ ___/
/ /___/ /_/ / / / / / / /_/ / /_/ (__  )  __/ /
\____/\____/_/ /_/ /_/ .___/\____/____/\___/_/
                    /_/
Composer version 2.3.5 2022-04-13 16:43:00

Usage:
  command [options] [arguments]

Options:
  -h, --help                     Display help for the given command. When no command is given display help for the list command
  -q, --quiet                    Do not output any message
  -V, --version                  Display this application version
      --ansi|--no-ansi           Force (or disable --no-ansi) ANSI output
  -n, --no-interaction           Do not ask any interactive question
      --profile                  Display timing and memory usage information
      --no-plugins               Whether to disable plugins.
      --no-scripts               Skips the execution of all scripts defined in composer.json file.
  -d, --working-dir=WORKING-DIR  If specified, use the given directory as working directory.
      --no-cache                 Prevent use of the cache
  -v|vv|vvv, --verbose           Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

 - [ ] - composer install
 - [ ] - npm install
 - [ ] - patikriname ar atliktas SETUP .env, jeigu .env nėra, ieškome .enc.example ir pervadiname į .env, <br> **.env SETUP EXAMPLE:**
```mysql
DB_CONNECTION=mysql
DB_HOST=localhost
DB_PORT=3306
DB_DATABASE=amspauda
DB_USERNAME=root
DB_PASSWORD=dbpassword
```
 - [ ] - php artisan migrate --seed
 - [ ] - php artisan optimise

## Start allready existing project

<ol>
 <li>php artisan serve</li>
 <ol>
  <li>open url: Server running on</li>
 </ol>
 <li>npm run dev</li>
 <li>if project doesn't start properly, try: php artisan optimize</li>
</ol>
 <img alt="Shows an illustrated sun in light mode and a moon with stars in dark mode." src="https://user-images.githubusercontent.com/25423296/163456779-a8556205-d0a5-45e2-ac17-42d089e3c3f8.png">

- [ ] - https://linuxhint.com/restart-mysql-in-ubuntu/
- [ ] - MySQL EXIT Secure install terminal - https://stackoverflow.com/questions/72248776/how-can-i-exit-from-mysql-secure-installation
- [ ] - 'Access denied for user 'root'@'localhost' - https://stackoverflow.com/questions/41645309/mysql-error-access-denied-for-user-rootlocalhost
- [ ] - Uninstall MySQL - https://askubuntu.com/questions/172514/how-do-i-uninstall-mysql
- [ ] - https://exerror.com/failed-error-set-password-has-no-significance-for-user-rootlocalhost-as-the-authentication-method-used-doesnt-store-authentication-data-in-the-mysql-server/
- [ ] - How to Fix 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)' - https://phoenixnap.com/kb/mysql-server-through-socket-var-run-mysqld-mysqld-sock-2
