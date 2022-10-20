<p align="center"><img alt="Shows an illustrated sun in light mode and a moon with stars in dark mode." src="https://laravel.com/img/logomark.min.svg"></p>
<h1 align="center">
# Hot To Start Laravel Project
</h1>

## Start from scratch
 - [ ] - install composer [open setup link](https://www.digitalocean.com/community/tutorials/how-to-install-composer-on-ubuntu-22-04-quickstart). or follow these steps"
### Step 1 — Install Dependencies
```bash
sudo apt update
sudo apt install php-cli unzip
```
### Step 2 — Download and Install Composer
Make sure you’re in your home directory, then retrieve the Composer installer using curl:
```bash
cd ~
curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
```
Using curl, fetch the latest signature and store it in a shell variable:
```bash
HASH=`curl -sS https://composer.github.io/installer.sig`
```
Now execute the following PHP code to verify that the installation script is safe to run:
```bash
php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
```
You’ll see the following output:
```bash
Installer verified
```

<h2> </h2>**Note**: _If the output says Installer corrupt, you’ll need to repeat the download and verification process until you have a verified installer._ 

### Step 1 — Install Dependencies
```bash
sudo apt update
sudo apt install php-cli unzip
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
