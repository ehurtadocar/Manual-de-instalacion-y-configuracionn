1. Abrir el enlace de instalacion del archivo
[.zip](https://github.com/rusben/smx-m08/blob/main/docs/installacio-clouds.md)

2. Hacer click donde pone: "Heu de baixar el .zip de ownCloud Server"

3. Abrir la carpeta de archivos donde esta guardado el archivo .zip y cambiar el nombre a: "owncloud"

4. Abrir un terminal de Linux y seguir los siguientes pasos:

1. Preparar el Sistema
```bash
sudo apt install software-properties-common -y
```
```bash
LC_ALL=C.UTF-8 sudo add-apt-repository ppa:ondrej/php -y
```
```bash
sudo apt update
```

2. Instalar PHP
```bash
sudo apt install php7.4 -y
```
```bash
sudo apt install -y php libapache2-mod-php7.4
```
```bash
sudo apt install -y php7.4-fpm php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-gd php7.4-xml php7.4-intl php7.4-mysql php7.4-cli php7.4-ldap php7.4-zip php7.4-curl
```
```bash
sudo update-alternatives --config php
```


3. Configurar Apache
```bash
sudo a2enmod proxy_fcgi setenvif
```
```bash
sudo a2enconf php7.4-fpm
```
```bash
sudo service apache2 restart
```

4. Actualizar el Sistema y Configurar MySQL
```bash
sudo apt update
```
```bash
sudo apt upgrade
```
```bash
sudo apt install -y apache2
```
```bash
sudo apt install -y mysql-server
```
```bash
sudo apt install -y php libapache2-mod-php
```
```bash
sudo apt install -y php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl
```
```bash
sudo systemctl restart apache2
```
```bash
sudo mysql
```
Dentro de MySQL, crea una base de datos
```bash
CREATE DATABASE bbdd;
```
```bash
CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
```bash
GRANT ALL ON bbdd.* to 'usuario'@'localhost';
```
```bash
exit
```
```bash
mysql -u usuario -p
```

5. Transferir Archivos y Configurar Permisos
```bash
sudo cp ~/Baixades/owncloud.zip /var/www/html
```
```bash
cd /var/www/html
```
```bash
sudo unzip owncloud.zip
```
```bash
sudo cp -R owncloud/. /var/www/html
```
```bash
sudo rm -rf owncloud/
```
```bash
sudo rm -rf /var/www/html/index.html
```
```bash
cd /var/www/html
```
```bash
sudo chmod -R 775 .
```
```bash
sudo chown -R usuario:www-data .
```
