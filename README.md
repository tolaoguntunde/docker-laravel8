## Deploying Laravel 8

- Deploying a laravel 8 (similar for older versions, except in few cases where the perhaps the PHP version changes) 

```bash
sudo apt update
```

- INSTALL APACHE

```bash
sudo apt install apache2 -y
```

```bash
sudo ufw allow in "Apache Full"
```

```bash
sudo systemctl start apache2
sudo systemctl enable apache2
```

- INSTALL PHP7.4

```bash
sudo add-apt-repository ppa:ondrej/php -y
sudo apt update
sudo apt -y install php7.4 libapache2-mod-php7.4 php7.4-bcmath php7.4-json php7.4-mbstring php7.4-xml php7.4-zip unzip php7.4-mysql php7.4-gd
```

- install composer
```bash
cd ~
curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
```
```bash
HASH=`curl -sS https://composer.github.io/installer.sig`
```

```bash
php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
```

```bash
sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```
- now composer has been installed

- CLONE REPO

```bash
cd /var/www/html
sudo rm index.html
sudo git clone https://github.com/slimprepdevops/docker-laravel8.git .
```

- INSTALL APPLICAITON DEPENDENCIES


```bash
sudo chown -R $USER:$USER /var/www/html
composer install
```
- enable applicaiton env

```bash
cp .env.example .env
```

```bash
php artisan key:gen
```

- CONFIGURE PERMISSIONS

```bash
sudo chown -R www-data:www-data /var/www/html
sudo chmod -R 755 /var/www/html
sudo chmod -R 775 /var/www/html/storage
```

- CONFIGURE APACHE DIRECTORY

```bash
sudo nano /etc/apache2/available-sites/000-default.conf
```
- change the Document root from `/var/www/html ` to `/var/www/html/public`
    - press `ctrl` + `keyboard x` on your keyboard to save (sometimes `ctrl` + `s` works just fine)
    - ensure to exit also

```bash
sudo systemctl reload apache2
sudo systemctl restart apache2
```
