[config]: /config
[config/default]: /config/default
[config/mysql]: /config/mysql
[config/php]: /config/php
[config/vhosts]: /config/vhosts

[config/default/php/php.ini-development]: /config/default/php/php.ini-development
[config/default/php/php.ini-production]: /config/default/php/php.ini-production

[config/php/php.ini]: /config/php/php.ini


[src]: /src



**Contenidos**
- [1. Servidor Apache, PHP, MySQL y phpMyAdmin](#1-servidor-apache-php-mysql-y-phpmyadmin)
    - [1.1. Apache y PHP](#11-apache-y-php)
    - [1.2. MySQL](#12-mysql)
    - [1.3. phpMyAdmin](#13-phpmyadmin)
- [2. Configuración](#2-configuración)
    - [2.1. Apache](#21-apache)
    - [2.2. MySQL](#22-mysql)
    - [2.3. PHP](#23-php)
    - [2.4. phpMyAdmin](#24-phpmyadmin)
- [3. Añadir archivos](#3-añadir-archivos)
- [4. Ejecutar](#4-ejecutar)


# 1. Servidor Apache, PHP, MySQL y phpMyAdmin
Permite levantar rápidamente un servidor WEB Apache con PHP, MySQL y phpMyAdmin

## 1.1. Apache y PHP
- Se utiliza la imagen `php:8.2-apache`

## 1.2. MySQL
- Se utiliza la imagen `mysql:8.4.0`

## 1.3. phpMyAdmin
- Se utiliza la imagen `phpmyadmin:5.2.1`


# 2. Configuración
- En [config] se almacenan los **archivos de configuración** de **Virtual Hosts** (Apache) ([config/vhosts]), **PHP** ([config/php]) y **MySQL** ([config/mysql])
- En [config/default] se almacenan los archivos de configuración **por defecto**

## 2.1. Apache
En [config/vhosts] se puede modificar los `sites-enabled` del servidor Apache. ***\*Se debe crear el archivo***

## 2.2. MySQL
- Modificar la variable de entorno `MYSQL_ROOT_PASSWORD` (**\<password\>**) para establecer la contraseña del usuario **root**

## 2.3. PHP
En [config/php] se puede modificar el archivo. Recomendable copiar el contenido de [config/default/php/php.ini-development] o [config/default/php/php.ini-production] en [config/php/php.ini] y modificar las variables que se deseen, por ejemplo:
- **memory_limit**: Limita la memoría máxima utilizada por un script
    - `-1`: Quita el límite ***\*No recomendable***
    - `<numero>M`: Número en MegaBytes a limitar (***\*128M***)
- **upload_max_filesize**
    - `<numero>M`: Número en MegaBytes máximo de un fichero subido (***\*25M***)
- **post_max_size**
    - `<numero>M`: Número en MegaBytes máxmio de un fichero a descargar (***\*25M***)
- **max_execution_time**
    - `<numero>`: Número en segundos máximos que puede ejecutar un script (***\*60***)


## 2.4. phpMyAdmin
- Modificar las variables de entorno
    - `PMA_HOST`: Host de la BBDD (En este ejemplo **db**)
    - `PMA_USER`: Usuario phpMyAdmin (Descomentar la línea y modificar `<usuario>`)
    - `PMA_PASSWORD`: Contrasñea del usuario phpMyAdmin (Descomentar la línea y modificar `<password>`)

# 3. Añadir archivos
Para añadir los **archivos web**, almacenarlos en [src]

# 4. Ejecutar
- **Construir**: `docker compose up -d --build`
- **Destruir**: `docker compose down`
- **Iniciar** (si existe): `docker compose start`
- **Detener** sin eliminar: `docker compose stop`
