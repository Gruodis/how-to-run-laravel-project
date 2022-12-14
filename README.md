<p align="center"><img alt="Shows an illustrated sun in light mode and a moon with stars in dark mode." src="https://laravel.com/img/logomark.min.svg"></p>
<h3 align="center">
# Runing Laravel Project
</h3>

<h1 align="center"> Composer & MySQL setup.</h1>


  - Essential commands:
    - [DBeaver](#dbeaver)
    - [PHP](#php)
      - [install multiple PHP versions](#change-php-version)
      - [change PHP versions](#install-php-v74)
    - [MySql](#mysql)
  - [Install Composer](#computer-to-install-composer-open-setup-link-or-follow-these-steps)
  - [Install MySQL](#computer-to-install-mysql-use-this-linkrecommended-or-quick-start-guidenot-recommended-or-follow-these-steps)
    - [Configure MySQL](#wrench-configuring-mysql)
    - [Final Steps MySQL](#computer-mysql-setup-final-step-securing-mysql)
  - [If Composer & MySQL Installed](#computer-if-composer--mysql-installed)
  - [Start Project](#computer-start-existing-project)
  - [If something fails](#bangbang-if-project-doesnt-start-properly-try)

<br>

## Laravel and Browser sync:

Full article is: [here](https://joncgrubb.github.io/2017/11/BrowserSync-With-Laravel.html)

Or just instead of:
```bash
mix.js('resources/assets/js/app.js', 'public/js')
 .sass('resources/assets/sass/app.scss', 'public/css');
```

like this:
```bash
mix.js('resources/assets/js/app.js', 'public/js')
   .sass('resources/assets/sass/app.scss', 'public/css')
   .browserSync('http://localhost:8000');
```


***

<br>

# Essentials:

<p align="center"><img alt="DBeaver." width="150" src="https://upload.wikimedia.org/wikipedia/commons/b/b5/DBeaver_logo.svg"></p>
<p align="center">
  if Yoy decide to use DBeaver for MySQL, <b>ONLY USE</b>
  <a href="https://dbeaver.io/download"  target=”_blank”>[Community version]</a>
</p>

# DBeaver
  - Local Client info
    - **ID/PATH/NAME:** ```/usr/bin```
    - **Product Name:** MySQL/MariaDB

<br>

---

<br>
<p align="center"><img alt="php" width="150" src="https://upload.wikimedia.org/wikipedia/commons/2/27/PHP-logo.svg"></p>

# PHP
  
  - **Regenerate** thumbnails:
  
      ```bash
      php artisan media-library:regenerate
      ```
      
  - **DISPLAY IMAGES** with proper url:

      ```bash
      php artisan storage:link
      ```   

  -  After local project files update(``git pull upstream master``):

      ```bash
      composer update
      ```
      ```bash
      php artisan optimize:clear
      ```

  - After project Database update:

      ```bash
      php artisan migrate
      ```
      ```bash
      php artisan optimize:clear
      ```

  - Extra - to export vendors lib
      ```bash
      php artisan vendor:publish
      ```
      
  <br>
  
## **Multiple PHP versions**:

  - ### **Step 1**: <small>System Update</small>
    ```bash
    sudo apt-get update
    ```
    ```bash
    sudo apt-get upgrade
    ```
  
  <br>
  
  - **Step 2**: Installing Multiple PHP Versions on Ubuntu 22.04
    ```bash
    sudo apt install software-properties-common
    - OR
    sudo apt install software-properties-common apt-transport-https -y
    ```
    ```bash
    sudo add-apt-repository ppa:ondrej/php
    ```
    ```bash
    sudo apt update
    ```
    ```bash
    sudo apt upgrade
    ```
    
  <br>
 

## **Install PHP v7.4**
  - Install PHP 7.4 using the following command:

  ```bash
  sudo apt-get install php7.4 php7.4-fpm
  sudo apt install php7.4 php7.4-fpm libapache2-mod-fcgid
  ```
    
  - And install some common PHP7.4 extensions:
    ```bash
    sudo apt-get install php7.4-zip php7.4-mysql php7.4-mbstring php7.4-xml php7.4-gd php7.4-curl
    
    sudo apt-get install php7.4-common php7.4-mysql php7.4-xml php7.4-xmlrpc php7.4-curl php7.4-gd php7.4-imagick php7.4-cli php7.4-dev php7.4-imap php7.4-mbstring php7.4-opcache php7.4-soap php7.4-zip php7.4-intl -y

    ```
    
  <br>
  
  - Check Check PHP loaded modules:

    ```bash
    php -m
    ```
    
  <br>
  
  - Check Active PHP Version:
 
    ```bash
    php -v
    ```
    
  <br>
  
### Switch Default PHP Version for CLI

```bash
sudo update-alternatives --config php
```
    
  > To change the default version, enter the number that matches the appropriate version you want to make as the default and press **ENTER**.
    
  <br>
 
  
  - **You can execute the command below to change the version straight away:**
    ```bash
    sudo update-alternatives --set php /usr/bin/php7.4
    ```
  <br>
  
## Uninstall PHP and remove Ondrej PPA

> If you don’t require the PHP7.4 and Ondrej PPA anymore on your Ubuntu 22.04 then we can remove them as well. Here are the commands to follow:

  ```bash
  sudo apt autoremove --purge php7.4
  ```
    
> To remove PPA, **Run the following command**:

  ```bash
  sudo add-apt-repository --remove ppa:ondrej/php -y
  ```
    
<br> 
   
  ## :bangbang: FIX Errors
  
  After PHP version change can't update OS propperly: PHP 8.1 Error _( unmet dependencies )_ FIX

  ```bash
  The following packages have unmet dependencies:
  php8.1-gd: Depends: php8.1-common (= 8.1.2-1ubuntu2.8) but 8.1.12-1+ubuntu22.04.1+deb.sury.org+1 is to be installed
  ```
  - Run:
    ```bash
    sudo apt-get install -y php8.1-cli php8.1-common php8.1-mysql php8.1-zip php8.1-gd php8.1-mbstring php8.1-curl php8.1-xml php8.1-bcmath
    ```
  - If You get output:
    ```bash
    Some packages could not be installed. This may mean that you have
    requested an impossible situation or if you are using the unstable
    distribution that some required packages have not yet been created
    or been moved out of Incoming.
    The following information may help to resolve the situation:

    The following packages have unmet dependencies:
     php8.1-gd : Depends: libgd3 (>= 2.3.3) but 2.3.0-2ubuntu2 is to be installed
    E: Unable to correct problems, you have held broken packages.
    ```
  - Run:
    ```bash
    sudo apt-get install libgd3
    ```
    ```bash
    sudo apt-get install -y php8.1-cli php8.1-common php8.1-mysql php8.1-zip php8.1-gd php8.1-mbstring php8.1-curl php8.1-xml php8.1-bcmath
    ```
    
    ```bash
    sudo apt autoremove
    ```
    ```bash
    php -v
    ```


<br />
<br />
  
    
<p align="center"><img alt="DBeaver." src="https://upload.wikimedia.org/wikipedia/en/thumb/d/dd/MySQL_logo.svg/150px-MySQL_logo.svg.png"></p>

# **MySQL**:

  - Login to mysql as user(-u) root with password(-p):
  - ```bash
    mysql -u root -p
    ```
  - To check MySQL version/status:
  - ```bash
    mysql --version
    sudo service mysql status
    ```
  - To start/restart/stop MySQL:
  - ```bash
    sudo service mysql start
    ```
    ```bash
    sudo service mysql restart
    ```
    ```bash
    sudo service mysql stop
    ```
    
    <br />
    <br />
  - Show MySQL Databases
    ```mysql
    SHOW DATABASES;
    ```
    <br />
    
  - DELETE Database
    ```mysql
    DROP DATABASE my_dabase;
    ```
    <br />
      
  - CREATE Database
    ```mysql
    CREATE DATABASE my_dabase;
    ```
    <br />
    <br />
  - RESTORE/IMOPRT .sql
    _Database must be created and **EMPTY**, then run_:
    ```mysql
    USE my_dabase;
    ```
    ```mysql
    SOURCE /home/user/Downloads/my_database.sql;
    ```
    
  - To exit >mysql:
  - ```bash
    exit
    ```
    
<br>
<br>

<p align="center"><img alt="DBeaver." width="150" src="https://upload.wikimedia.org/wikipedia/commons/5/51/Windows_Terminal_logo.svg"></p>
    
# DIR:
  - ```cd ~```  & ```cd```  is used to change directory to the home directory. 
  - ```bash
    cd ~
    cd
    ```
  - ```cd..```  is used to move to the parent directory of current directory, or the directory one level up from the current directory. “..” represents parent directory.
  - ```bash
    cd..
    ```
  - ```pwd```  stands for Print Working Directory. It prints the path of the working directory, starting from the root.
  - ```bash
    pwd
    ```

<br />
<br />

## :computer: To Install Composer [open setup link](https://www.digitalocean.com/community/tutorials/how-to-install-composer-on-ubuntu-22-04-quickstart) or follow these steps
- ### Step 1: Install Dependencies
  - ```bash
    sudo apt update
    sudo apt install php-cli unzip
      ```
<hr />
    
- ### Step 2: Download and Install Composer
  - For ***Windows OS*** just navigate to the official [composer website](https://getcomposer.org/download/).
  - Make sure you’re in your home directory, then retrieve the Composer installer using curl:
    ```bash
    cd ~
    curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
    ```
  - Using curl, fetch the latest signature and store it in a shell variable:
    ```bash
    HASH=`curl -sS https://composer.github.io/installer.sig`
    ```
  - Now execute the following PHP code to verify that the installation script is safe to run:
    ```bash
    php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
    ```
  - You’ll see the following output:
    ```bash
    Installer verified
    ```
  - > **Note:**
_If the output says Installer corrupt, you’ll need to repeat the download and verification process until you have a verified installer._

  - The following command will download and install Composer as a system-wide command named **composer**, under **/usr/local/bin**:
    ```bash
    sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
    ```
  - You’ll see output similar to this:
    ```bash
    Output
    All settings correct for using Composer
    Downloading...

    Composer (version 2.3.5) successfully installed to: /usr/local/bin/composer
    Use it: php /usr/local/bin/composer
    ```
<hr />
    
- ### To test your installation, run:
  - ```bash
    composer
    ```
- ### Output:
  - ```bash
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
    
<br />
<hr />
<br />

## :computer: To Install MySQL [use this link](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04)(recommended) or [quick start guide](https://www.digitalocean.com/community/tutorials/how-to-install-composer-on-ubuntu-22-04-quickstart)(NOT recommended) or follow these steps:
- #### Step 1: Update/Upgrade Package Repository
    - ```bash
      sudo apt update
      ```
    - ```bash
      sudo apt upgrade
      ```
- #### Step 2: Install MySQL
    - ```bash
      sudo apt install mysql-server
      ```

- #### Step 3: Check if MySQL was successfully installed by running:
    - ```bash
      mysql --version
      ```

- #### To start MySQL now:
    - ```bash
      sudo systemctl enable --now mysql.service
      ```

- #### To check is MySQL is running: 
    - ```bash
      systemctl status mysql.service
      ```
      
<br />
<hr />
<br />

## :wrench: Configuring MySQL
- ### Step 1:
   - First, open up the MySQL prompt:
    - ```bash
      sudo mysql
      ```
      
- ### Step 2:
   - Then run the following ALTER USER command to change the root user’s authentication method to one that uses a password. The following example changes the authentication method to mysql_native_password:
    - ```bash
      ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'mynewpassword';
      ```
      
- ### Step 3:
   - After making this change, exit the MySQL prompt:
     ```bash
     exit
     ```

#### :bangbang: If you get this ERROR after step above
> ERROR 1819 (HY000): Your password does not satisfy the current policy requirements

#### Posible solutions:
1. The first one is to Use a Strong Password Just Like Addy@789**$ This Password Will satisfy current policy requirements.
2. The second one is Just Uninstall validate_password plugin with these two commands:
   - first:
     ```bash
      mysql -h localhost -u root -p
      ```
   - and then:
     ```bash
     uninstall the plugin validate_password;
     ```
      
3. The third solution is You can set validate_password.policy to do so Just run:
   - first: 
     ```bash 
     sudo mysql 
     ```
   - and Then:
     ```bash 
     SET GLOBAL validate_password.policy=LOW; 
     ```

<br />
<hr />
<br />

## :computer: MySQL Setup FINAL Step: Securing MySQL
- #### Yoy can follow this [video](https://www.youtube.com/watch?v=3qD6zv7thdE&t=157s&ab_channel=ITProTV) for detailed info or follow these guidlines:

- ### Step 1:
   - Following that, you can run the mysql_secure_installation script without issue:
     ```bash
     sudo  mysql_secure_installation
     ```

- ### Step 2:
   - Once the security script completes, you can then reopen MySQL and change the root user’s authentication method back to the default, auth_socket. To authenticate as the root MySQL user using a password, run this command:
     ```bash
     mysql -u root -p
     ```
- ### Step 3:
   - Then go back to using the default authentication method using this command:
     ```bash
     ALTER USER 'root'@'localhost' IDENTIFIED WITH auth_socket;
     ```
   - This will mean that you can once again connect to MySQL as your root user using the sudo mysql command.

<br />
<hr />
<br />

## :computer: IF Composer & MySQL installed

- ## First of All
  - Install php curl
    ```bash
    sudo apt-get install php-curl
    ```

- ## Step 1:  
  - Install dependencies as specified in the **composer.lock** file:
    ```bash 
    composer install
    ```
    
  - **:interrobang:** IF You get dependencies Error like in example below:
    ```bash
    Updating dependencies
    Your requirements could not be resolved to an installable set of packages.

      Problem 1
        - tijsverkoyen/css-to-inline-styles 2.2.2 requires php ^5.5 || ^7.0 -> your php version (8.1.2) does not satisfy that requirement.
        - tijsverkoyen/css-to-inline-styles[2.2.3, ..., 2.2.x-dev] require ext-dom * -> it is missing from your system. Install or enable PHP's dom extension.....
    ```
    Try this:
    
    ```bash
    sudo apt install php-zip
    ```
    ```bash
    sudo apt-get install php-mbstring
    ```
    ```bash
    sudo apt install php-xml
    ```
  - Install NPM dependencies:
    ```bash
    npm install
    ```

- ## Step 2:
  - Check if **.env** exists & fill in details required **.env** SETUP EXAMPLE:
    ```mysql
      DB_CONNECTION=mysql
      DB_HOST=localhost
      DB_PORT=3306
      DB_DATABASE=db_name
      DB_USERNAME=root
      DB_PASSWORD=dbpassword
      ```
  - ***:interrobang:*** If **.env** doesn't exist, find **.env.example** & rename to **.env**. 
    ```bash
    cp .env.example .env
    ```
- ## Step 3 :bangbang: IMPORTANT! 
  - Create database with same name as in **.env** file - **"db_name"**. For that You can use **DBeaver** or commmand line:
      ```bash
      mysql -u root -p
      ```
      After You enter credentials output should look like this:
      ```bash
      mysql>
      ```
      Now we can create new database _(this command only creates the database **db_name** if a database of that name does not already exist)_ :
      ```bash
      CREATE DATABASE IF NOT EXISTS db_name;
      ```

- ## Step 4:
   - ```bash
      php artisan migrate --seed
     ```
   - ```bash
      php artisan optimize
      ```
- ## Step 5:
   - ```bash
      php artisan serve
     ```
   - ```bash
      npm run dev
      ```
- > ## :interrobang:  If You get Error "_The only supported ciphers are..._" 
- after ```sudo php artisan key:generate``` remove key from APP_KEY=key located in **.env** and then run:

   - ```bash
      sudo php artisan config:cache
      sudo php artisan key:generate
      php artisan optimize
      ```
<br />
<hr />
<br />

## :computer: Start existing project:

- ### Run easch command in separate terminal window:
  - ```bash
    php artisan serve
    ```
  - ```bash
    npm run dev
    ```
>
> :earth_africa: URL is found on ***"php artisan server"*** terminal: Server running on [IP:port]
> 

## :bangbang: If project doesn't start properly, try: 
  - ```bash
    php artisan optimize
    ```

<br />
<hr />
<br />

## :pill: Other useful links:

  - [Restart MySQL Server](https://linuxhint.com/restart-mysql-in-ubuntu/)
  - [MySQL EXIT Secure install terminal](https://stackoverflow.com/questions/72248776/how-can-i-exit-from-mysql-secure-installation)
  - ['Access denied for user 'root'@'localhost'](https://stackoverflow.com/questions/41645309/mysql-error-access-denied-for-user-rootlocalhost)
  - [Uninstall MySQL](https://askubuntu.com/questions/172514/how-do-i-uninstall-mysql)
  - [User root password ERROR](https://exerror.com/failed-error-set-password-has-no-significance-for-user-rootlocalhost-as-the-authentication-method-used-doesnt-store-authentication-data-in-the-mysql-server/)
  - [How to Fix 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'](https://phoenixnap.com/kb/mysql-server-through-socket-var-run-mysqld-mysqld-sock-2)
