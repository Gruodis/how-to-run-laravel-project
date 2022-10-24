<p align="center"><img alt="Shows an illustrated sun in light mode and a moon with stars in dark mode." src="https://laravel.com/img/logomark.min.svg"></p>
<h3 align="center">
# Runing Laravel Project
</h3>

<h1 align="center"> Composer & MySQL setup.</h1>


  - [Install Composer](#computer-to-install-composer-open-setup-link-or-follow-these-steps)
  - [Install MySQL](#computer-to-install-mysql-use-this-linkrecommended-or-quick-start-guidenot-recommended-or-follow-these-steps)
  - [Configure MySQL](#wrench-configuring-mysql)
  - [Final Steps MySQL](#computer-mysql-setup-final-step-securing-mysql)
  - [If Composer & MySQL Installed](#computer-if-composer--mysql-installed)
  - [Start Project](#computer-start-existing-project)
  - [If something fails](#bangbang-if-project-doesnt-start-properly-try)

<br />
<hr />
<br />

### Linux essential DIR nav cmd:


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
<hr />
<br />

## :computer: To Install Composer [open setup link](https://www.digitalocean.com/community/tutorials/how-to-install-composer-on-ubuntu-22-04-quickstart) or follow these steps
- ### Step 1: Install Dependencies
  - ```bash
    sudo apt update
    sudo apt install php-cli unzip
      ```
<hr />
    
- ### Step 2: Download and Install Composer
  - Make sure you’re in your home directory, then retrieve the Composer installer using curl:
  - ```bash
    cd ~
    curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
    ```
  -  — Using curl, fetch the latest signature and store it in a shell variable:
  - ```bash
    HASH=`curl -sS https://composer.github.io/installer.sig`
    ```
  - Now execute the following PHP code to verify that the installation script is safe to run:
  - ```bash
    php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
    ```
  - You’ll see the following output:
  - ```bash
    Installer verified
    ```
  - > **Note:**
_If the output says Installer corrupt, you’ll need to repeat the download and verification process until you have a verified installer._

  - The following command will download and install Composer as a system-wide command named **composer**, under **/usr/local/bin**:
  - ```bash
    sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
    ```
  - You’ll see output similar to this:
  - ```bash
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
      
- #### Ensure that the server is running using the systemctl start command:
    - ```bash
      sudo systemctl start mysql.service
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
    - ```bash
      exit
      ```

#### :bangbang: If you get this ERROR after step above
> ERROR 1819 (HY000): Your password does not satisfy the current policy requirements

#### Posible solutions:
1. The first one is to Use a Strong Password Just Like Addy@789**$ This Password Will satisfy current policy requirements.
2. The second one is Just Uninstall validate_password plugin with these two commands:
   -  ```bash
      mysql -h localhost -u root -p
      ```
   - and then:
   -  ```bash
      uninstall the plugin validate_password;
      ```
      
3. The third solution is You can set validate_password.policy to do so Just run:
   -  ```bash 
      sudo mysql 
      ```
   - and Then:
   -  ```bash 
       SET GLOBAL validate_password.policy=LOW; 
       ```

<br />
<hr />
<br />

## :computer: MySQL Setup FINAL Step: Securing MySQL
- #### Yoy can follow this [video](https://www.youtube.com/watch?v=3qD6zv7thdE&t=157s&ab_channel=ITProTV) for detailed info or follow these guidlines:

- ### Step 1:
   - Following that, you can run the mysql_secure_installation script without issue:
    - ```bash
      sudo  mysql_secure_installation
      ```

- ### Step 2:
   - Once the security script completes, you can then reopen MySQL and change the root user’s authentication method back to the default, auth_socket. To authenticate as the root MySQL user using a password, run this command:
    - ```bash
      mysql -u root -p
      ```
- ### Step 3:
   - Then go back to using the default authentication method using this command:
    - ```bash
      ALTER USER 'root'@'localhost' IDENTIFIED WITH auth_socket;
      ```
    - This will mean that you can once again connect to MySQL as your root user using the sudo mysql command.

<br />
<hr />
<br />

## :computer: IF Composer & MySQL installed

#### BEFORE START
- Install php curl
  - ```bash
    sudo apt-get install php-curl
    ```

- ## Step 1:  
  - Install dependencies as specified in the composer.lock file:
  - ```bash 
    composer install
    ```
  - ```bash
    aurelijus@pop-os:~/PhpstormProjects/am-spauda$ composer install
    No composer.lock file present. Updating dependencies to latest instead of installing from lock file. See https://getcomposer.org/install for more information.
    Loading composer repositories with package information
    Your GitHub credentials are required to fetch private repository metadata (https://github.com/OneSoftIO/onesoft-lang.git)
    When working with _public_ GitHub repositories only, head to https://github.com/settings/tokens/new?scopes=&description=Composer+on+pop-os+2022-10-23+2238 to retrieve a token.
    This token will have read-only permission for public information only.
    When you need to access _private_ GitHub repositories as well, go to https://github.com/settings/tokens/new?scopes=repo&description=Composer+on+pop-os+2022-10-23+2238
    Note that such tokens have broad read/write permissions on your behalf, even if not needed by Composer.
    Tokens will be stored in plain text in "/home/aurelijus/.config/composer/auth.json" for future use by Composer.
    For additional information, check https://getcomposer.org/doc/articles/authentication-for-private-packages.md#github-oauth
    Token (hidden): 
    Token stored successfully.
    Info from https://repo.packagist.org: #StandWithUkraine
    Updating dependencies
    Your requirements could not be resolved to an installable set of packages.

      Problem 1
        - tijsverkoyen/css-to-inline-styles 2.2.2 requires php ^5.5 || ^7.0 -> your php version (8.1.2) does not satisfy that requirement.
        - tijsverkoyen/css-to-inline-styles[2.2.3, ..., 2.2.x-dev] require ext-dom * -> it is missing from your system. Install or enable PHP's dom extension.
        - diglactic/laravel-breadcrumbs[v8.0.0, ..., v8.0.1] require laravel/framework ^6.0 || ^7.0 || ^8.0 || ^9.0 -> satisfiable by laravel/framework[v9.19.0, ..., 9.x-dev].
        - laravel/framework[v9.34.0, ..., 9.x-dev] require tijsverkoyen/css-to-inline-styles ^2.2.5 -> satisfiable by tijsverkoyen/css-to-inline-styles[2.2.5, 2.2.x-dev].
        - laravel/framework[v9.19.0, ..., v9.33.0] require tijsverkoyen/css-to-inline-styles ^2.2.2 -> satisfiable by tijsverkoyen/css-to-inline-styles[2.2.2, ..., 2.2.x-dev].
        - Root composer.json requires diglactic/laravel-breadcrumbs ^8.0 -> satisfiable by diglactic/laravel-breadcrumbs[v8.0.0, v8.0.1].

    To enable extensions, verify that they are enabled in your .ini files:
        - /etc/php/8.1/cli/php.ini
        - /etc/php/8.1/cli/conf.d/10-opcache.ini
        - /etc/php/8.1/cli/conf.d/10-pdo.ini
        - /etc/php/8.1/cli/conf.d/20-calendar.ini
        - /etc/php/8.1/cli/conf.d/20-ctype.ini
        - /etc/php/8.1/cli/conf.d/20-curl.ini
        - /etc/php/8.1/cli/conf.d/20-exif.ini
        - /etc/php/8.1/cli/conf.d/20-ffi.ini
        - /etc/php/8.1/cli/conf.d/20-fileinfo.ini
        - /etc/php/8.1/cli/conf.d/20-ftp.ini
        - /etc/php/8.1/cli/conf.d/20-gettext.ini
        - /etc/php/8.1/cli/conf.d/20-iconv.ini
        - /etc/php/8.1/cli/conf.d/20-intl.ini
        - /etc/php/8.1/cli/conf.d/20-mbstring.ini
        - /etc/php/8.1/cli/conf.d/20-phar.ini
        - /etc/php/8.1/cli/conf.d/20-posix.ini
        - /etc/php/8.1/cli/conf.d/20-readline.ini
        - /etc/php/8.1/cli/conf.d/20-shmop.ini
        - /etc/php/8.1/cli/conf.d/20-sockets.ini
        - /etc/php/8.1/cli/conf.d/20-sysvmsg.ini
        - /etc/php/8.1/cli/conf.d/20-sysvsem.ini
        - /etc/php/8.1/cli/conf.d/20-sysvshm.ini
        - /etc/php/8.1/cli/conf.d/20-tokenizer.ini
    You can also run `php --ini` in a terminal to see which files are used by PHP in CLI mode.
    Alternatively, you can run Composer with `--ignore-platform-req=ext-dom` to temporarily ignore these required extensions.
    ```
    
  - ```bash 
    npm install
    ```

- ## Step 2:
  - Check if .env exists & fill in details required **.env SETUP EXAMPLE:**
  -  ```mysql
      DB_CONNECTION=mysql
      DB_HOST=localhost
      DB_PORT=3306
      DB_DATABASE=amspauda
      DB_USERNAME=root
      DB_PASSWORD=dbpassword
      ```
- ## :interrobang: If .env doesn't exist, find .env.example & rename to .env. 
  - ```bash
    cp .env.example .env
    ```

- ## Step 3:
   - ```bash
      php artisan migrate --seed
     ```
   - ```bash
      php artisan optimize
      ```
- ## Step 4:
   - ```bash
      php artisan serve
     ```
   - ```bash
      npm run dev
      ```
- ## > :wrench: If after ```sudo php artisan key:generate``` You get "***The only supported ciphers are...***" Error, remove key from APP_KEY=key located in **.env** and then run:

   - ```bash
      sudo php artisan key:generate
      sudo php artisan config:cache
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
