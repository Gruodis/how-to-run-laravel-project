<p align="center"><img alt="Shows an illustrated sun in light mode and a moon with stars in dark mode." src="https://laravel.com/img/logomark.min.svg"></p>
<h1 align="center">
# Hot To Start Laravel Project
</h1>

## Start from scratch
 - [ ] - install composer [GitHub Pages](https://www.digitalocean.com/community/tutorials/how-to-install-composer-on-ubuntu-22-04-quickstart). 

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
 <li>npm run dev </li>
 <li>if project doesn't start properly, try: php artisan optimise</li>
</ol>
 <img alt="Shows an illustrated sun in light mode and a moon with stars in dark mode." src="https://user-images.githubusercontent.com/25423296/163456779-a8556205-d0a5-45e2-ac17-42d089e3c3f8.png">

- [ ] - https://linuxhint.com/restart-mysql-in-ubuntu/
- [ ] - MySQL EXIT Secure install terminal - https://stackoverflow.com/questions/72248776/how-can-i-exit-from-mysql-secure-installation
- [ ] - 'Access denied for user 'root'@'localhost' - https://stackoverflow.com/questions/41645309/mysql-error-access-denied-for-user-rootlocalhost
- [ ] - Uninstall MySQL - https://askubuntu.com/questions/172514/how-do-i-uninstall-mysql
- [ ] - https://exerror.com/failed-error-set-password-has-no-significance-for-user-rootlocalhost-as-the-authentication-method-used-doesnt-store-authentication-data-in-the-mysql-server/
- [ ] - How to Fix 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)' - https://phoenixnap.com/kb/mysql-server-through-socket-var-run-mysqld-mysqld-sock-2
