# Práctica Docker Despliegue

Este documento describe los pasos de mi entendimiento en la arquitectura y la configuración de esta práctica.

## Arquitectura

La arquitectura ha sido bastante simple.  
Lo primero que hemos hecho ha sido definir dos redes:  
- La red de **frontend**, desde la cual se puede acceder a WordPress y phpMyAdmin.  
- La red de **backend**, desde la cual se puede acceder a la base de datos.  

Para realizar la conexión entre WordPress y phpMyAdmin con la base de datos, las hemos incluido en la red de backend.  
Con esto hemos conseguido una arquitectura desde la cual podemos acceder desde nuestra máquina local a los servicios del servidor frontend.

## Configuración

La configuración ha sido compleja, sobre todo la parte de investigar la configuración de `bitnami/wordpress`, la cual no era fácil de entender.  
Sin embargo, una vez añadidas las configuraciones de la base de datos, ha sido más sencillo.

### Configuraciones combinadas (MySQL y WordPress)

```env
# MySQL Configuration
ALLOW_EMPTY_PASSWORD=no
MYSQL_ROOT_PASSWORD=root_password
MYSQL_DATABASE=wordpress
MYSQL_USER=wordpress_user
MYSQL_PASSWORD=wordpress_password

# WordPress Configuration
WORDPRESS_DATABASE_HOST=db
WORDPRESS_DATABASE_PORT_NUMBER=3306
WORDPRESS_DATABASE_USER=wordpress_user
WORDPRESS_DATABASE_PASSWORD=wordpress_password
WORDPRESS_DATABASE_NAME=wordpress
```