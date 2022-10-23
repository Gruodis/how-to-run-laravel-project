<p align="center"><img alt="Shows an illustrated sun in light mode and a moon with stars in dark mode." src="https://laravel.com/img/logomark.min.svg"></p>
<h3 align="center">
# Runing Laravel Project
</h3>

<h1 align="center"> Composer & MySQL setup.</h1>

<br />
<hr />
<br />

## To Install Composer [open setup link](https://www.digitalocean.com/community/tutorials/how-to-install-composer-on-ubuntu-22-04-quickstart) or follow these steps:
- ### Step 1 — Install Dependencies
  - ```bash
    sudo apt update
    sudo apt install php-cli unzip
    ```
- ### Step 2 — Download and Install Composer
  - #### Make sure you’re in your home directory, then retrieve the Composer installer using curl:
  - ```bash
    cd ~
    curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
    ```
  - #### Using curl, fetch the latest signature and store it in a shell variable:
  - ```bash
    HASH=`curl -sS https://composer.github.io/installer.sig`
    ```
  - #### Now execute the following PHP code to verify that the installation script is safe to run:
  - ```bash
    php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
    ```
  - #### You’ll see the following output:
  - ```bash
    Installer verified
    ```
  - > **Note:**
_If the output says Installer corrupt, you’ll need to repeat the download and verification process until you have a verified installer._

  - #### The following command will download and install Composer as a system-wide command named **composer**, under **/usr/local/bin**:
  - ```bash
    sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
    ```
  - #### You’ll see output similar to this:
  - ```bash
    Output
    All settings correct for using Composer
    Downloading...

    Composer (version 2.3.5) successfully installed to: /usr/local/bin/composer
    Use it: php /usr/local/bin/composer
    ```
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

# To Install MySQL [use this link](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04)(recommended) or [quick start guide](https://www.digitalocean.com/community/tutorials/how-to-install-composer-on-ubuntu-22-04-quickstart)(NOT recommended) or follow these steps:
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

# Configuring MySQL
- ### Step 1:
   - #### First, open up the MySQL prompt:
    - ```bash
      sudo mysql
      ```
      
- ### Step 2:
   - #### Then run the following ALTER USER command to change the root user’s authentication method to one that uses a password. The following example changes the authentication method to mysql_native_password:
    - ```bash
      ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'mynewpassword';
      ```
      
- ### Step 3:
   - #### After making this change, exit the MySQL prompt:
    - ```bash
      exit
      ```

#### If you get this ERROR after step above
> ERROR 1819 (HY000): Your password does not satisfy the current policy requirements

#### Posible solutions:
1. The first one is to Use a Strong Password Just Like Addy@789**$ This Password Will satisfy current policy requirements.
2. The second one is Just Uninstall validate_password plugin with these two commands:
   - mysql -h localhost -u root -p
   - and then
   - uninstall the plugin validate_password;
3. The third solution is You can set validate_password.policy to do so Just run:
   - sudo mysql
   - and Then
   - SET GLOBAL validate_password.policy=LOW;

<br />
<hr />
<br />

# MySQL Setup FINAL Step: Securing MySQL
- #### Yoy can follow this [video](https://www.youtube.com/watch?v=3qD6zv7thdE&t=157s&ab_channel=ITProTV) for detailed info or follow these guidlines:

- ### Step 1:
   - #### Following that, you can run the mysql_secure_installation script without issue:
    - ```bash
      sudo  mysql_secure_installation
      ```

- ### Step 2:
   - #### Once the security script completes, you can then reopen MySQL and change the root user’s authentication method back to the default, auth_socket. To authenticate as the root MySQL user using a password, run this command:
    - ```bash
      mysql -u root -p
      ```
- ### Step 3:
   - #### Then go back to using the default authentication method using this command:
    - ```bash
      ALTER USER 'root'@'localhost' IDENTIFIED WITH auth_socket;
      ```
    - This will mean that you can once again connect to MySQL as your root user using the sudo mysql command.
    - 
<br />
<hr />
<br />

# IF Composer & MySQL installed
- ## Step 1:  dependencies as specified in the composer.lock file
- composer install
- npm install
- patikriname ar atliktas SETUP .env, jeigu .env nėra, ieškome .enc.example ir pervadiname į .env, <br> **.env SETUP EXAMPLE:**
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

# Start existing project:

<ol>
 <li>php artisan serve</li>
 <ol>
  <li>open url: Server running on</li>
 </ol>
 <li>npm run dev</li>
 <li>if project doesn't start properly, try: php artisan optimize</li>
</ol>

<br />
<hr />
<br />

- [ ] - https://linuxhint.com/restart-mysql-in-ubuntu/
- [ ] - MySQL EXIT Secure install terminal - https://stackoverflow.com/questions/72248776/how-can-i-exit-from-mysql-secure-installation
- [ ] - 'Access denied for user 'root'@'localhost' - https://stackoverflow.com/questions/41645309/mysql-error-access-denied-for-user-rootlocalhost
- [ ] - Uninstall MySQL - https://askubuntu.com/questions/172514/how-do-i-uninstall-mysql
- [ ] - https://exerror.com/failed-error-set-password-has-no-significance-for-user-rootlocalhost-as-the-authentication-method-used-doesnt-store-authentication-data-in-the-mysql-server/
- [ ] - How to Fix 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)' - https://phoenixnap.com/kb/mysql-server-through-socket-var-run-mysqld-mysqld-sock-2
