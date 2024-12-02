# Install Apache

1. Update package list
    ```bash
    sudo apt update
    ```

2. Install Apache
    ```bash
    sudo apt install apache2
    ```

3. Check available firewall applications
    ```bash
    sudo ufw app list
    ```
    **Output:**
    Available applications:
    - Apache
    - Apache Full
    - Apache Secure
    - OpenSSH

4. Allow Apache through the firewall
    ```bash
    sudo ufw allow 'Apache'
    ```

5. Check Apache service status
    ```bash
    sudo systemctl status apache2
    ```
    You should now see the default Ubuntu Apache web page at:  
    [http://localhost/](http://localhost/)

6. Apache service commands:
    - Stop Apache:
        ```bash
        sudo systemctl stop apache2
        ```
    - Start Apache:
        ```bash
        sudo systemctl start apache2
        ```
    - Restart Apache:
        ```bash
        sudo systemctl restart apache2
        ```
    - Reload Apache:
        ```bash
        sudo systemctl reload apache2
        ```

7. Give permission to the HTML files:
    ```bash
    sudo chmod -R 777 /var/www/html
    ```

---

# Install MySQL

1. Install MySQL server:
    ```bash
    sudo apt install mysql-server
    ```

2. Check MySQL service status:
    ```bash
    sudo service mysql status
    ```

3. Login to MySQL:
    ```bash
    sudo mysql
    ```

4. Set root user password:
    ```sql
    ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root@123';
    ```

5. Login as root:
    ```bash
    mysql -u root -p
    ```

---

# Install PHPMyAdmin

1. Install PHPMyAdmin and required PHP modules:
    ```bash
    sudo apt install phpmyadmin php-mbstring php-zip php-gd php-json php-curl
    sudo apt install phpmyadmin
    ```

2. Enable the mbstring module:
    ```bash
    sudo phpenmod mbstring
    ```

3. Restart Apache:
    ```bash
    sudo systemctl restart apache2
    ```

4. Check PHPMyAdmin at this URL:
    [https://localhost/phpmyadmin/](https://localhost/phpmyadmin/)

5. Enable necessary Apache library:
    ```bash
    sudo apt install apache2 libapache2-mod-php8.1 -y
    ```

6. Configure Apache:
    - Navigate to `/etc/apache2`:
        ```bash
        cd /etc/apache2
        ```

    - Edit the `apache2.conf` file:
        ```bash
        sudo nano apache2.conf
        ```

    - In the opened file, change `AllowOverride None` to `AllowOverride All`:
        ```bash
        <Directory /var/www/>
            Options Indexes FollowSymLinks
            AllowOverride All              
            Require all granted
        </Directory>
        ```

    - Include PHPMyAdmin configuration:
        Add the following line to the end of the file:
        ```bash
        Include /etc/phpmyadmin/apache.conf
        ```

---

# Install PHP Versions

1. Update and upgrade packages:
    ```bash
    sudo apt update && sudo apt upgrade
    ```

2. Install software properties:
    ```bash
    sudo apt install software-properties-common
    ```

3. Add the PHP repository:
    ```bash
    sudo add-apt-repository ppa:ondrej/php
    ```

4. Update package list:
    ```bash
    sudo apt update
    ```

5. Install multiple PHP versions:
    ```bash
    sudo apt -y install php7.4
    sudo apt -y install php7.3
    sudo apt -y install php8.2
    sudo apt -y install php8.3
    sudo apt -y install php8.0
    sudo apt -y install php7.2
    sudo apt -y install php7.1
    ```

6. Switch between PHP versions:
    ```bash
    sudo update-alternatives --config php
    ```

7. Check the installed PHP version:
    ```bash
    php -v
    ```

---

