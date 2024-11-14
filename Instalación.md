1. Abrir el enlace de instalacion del archivo .zip 
[Archivo .zip](https://github.com/rusben/smx-m08/blob/main/docs/installacio-clouds.md)

2. Hacer click donde pone: "Heu de baixar el .zip de ownCloud Server"

3. Abrir la carpeta de archivos donde esta guardado el archivo .zip y cambiar el nombre a: "owncloud"

4. Abrir un terminal de Linux y seguir los siguientes pasos:

1. Preparar el Sistema

sudo apt install software-properties-common -y
LC_ALL=C.UTF-8 sudo add-apt-repository ppa:ondrej/php -y
sudo apt update

2. Instalar PHP

sudo apt install php7.4 -y
sudo apt install -y php libapache2-mod-php7.4
sudo apt install -y php7.4-fpm php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-gd php7.4-xml php7.4-intl php7.4-mysql php7.4-cli php7.4-ldap php7.4-zip php7.4-curl
sudo update-alternatives --config php

3. Configurar Apache

sudo a2enmod proxy_fcgi setenvif
sudo a2enconf php7.4-fpm
sudo service apache2 restart

4. Actualizar el Sistema y Configurar MySQL

sudo apt update
sudo apt upgrade
sudo apt install -y apache2
sudo apt install -y mysql-server
sudo apt install -y php libapache2-mod-php
sudo apt install -y php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl
sudo systemctl restart apache2
sudo mysql

Dentro de MySQL, crea una base de datos

CREATE DATABASE bbdd;
CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
GRANT ALL ON bbdd.* to 'usuario'@'localhost';
exit
mysql -u usuario -p

5. Transferir Archivos y Configurar Permisos

sudo cp ~/Baixades/owncloud.zip /var/www/html
cd /var/www/html
sudo unzip owncloud.zip
sudo cp -R owncloud/. /var/www/html
sudo rm -rf owncloud/
sudo rm -rf /var/www/html/index.html
cd /var/www/html
sudo chmod -R 775 .
sudo chown -R usuario:www-data .
