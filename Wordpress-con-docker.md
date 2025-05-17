# Práctica: Configuración de WordPress con Docker

## 1. Título  
Crear contenedores Docker para WordPress, MySQL y phpMyAdmin con persistencia de datos y red personalizada.

## 2. Tiempo de duración  
45 minutos

## 3. Fundamentos  
Docker permite crear entornos aislados para ejecutar servicios sin instalarlos directamente en el sistema operativo.  
En esta práctica configuramos una red Docker personalizada para comunicar varios contenedores (WordPress, MySQL y phpMyAdmin), creamos volúmenes para persistir los datos y garantizamos que los servicios puedan comunicarse de forma segura y estable.

## 4. Objetivos

### Objetivo general  
Levantar un sitio WordPress usando contenedores Docker, con base de datos MySQL y phpMyAdmin para gestión.

### Objetivos específicos  
1. Crear una red Docker para comunicación entre contenedores.  
2. Crear volúmenes Docker para persistencia de datos de WordPress y MySQL.  
3. Ejecutar los contenedores con configuración adecuada para que trabajen en conjunto.  
4. Acceder a WordPress y phpMyAdmin desde el navegador.

## 5. Repaso

Primero creamos una red llamada `wordpress-net` para conectar los contenedores.  
Luego generamos dos volúmenes: `wordpress-vol` para archivos de WordPress y `mysql-vol` para datos de MySQL.  
Después, creamos un contenedor MySQL con usuario, contraseña y base de datos definidos, usando el volumen para persistencia.  
A continuación, levantamos phpMyAdmin conectado a la base de datos, mapeando el puerto 8080 para su acceso web.  
Finalmente, creamos el contenedor WordPress vinculado a la base de datos MySQL y usando su volumen propio, expuesto en el puerto 8000.

---

## 6. Paso a Paso

### Crear la red Docker

```bash
docker network create wordpress-net
docker volume create wordpress-vol
docker volume create mysql-vol
```
  
2. Crear el contenedor MySQL

```bash
docker run -d \
  --name mysql-wp \
  --network wordpress-net \
  -e MYSQL_ROOT_PASSWORD=rootpass \
  -e MYSQL_DATABASE=wordpress \
  -e MYSQL_USER=wpuser \
  -e MYSQL_PASSWORD=wppass \
  -v mysql-vol:/var/lib/mysql \
  mysql:5.7
```
  
3. Crear el contenedor phpMyAdmin

```bash
docker run -d \
  --name phpmyadmin-wp \
  --network wordpress-net \
  -e PMA_HOST=mysql-wp \
  -p 8080:80 \
  phpmyadmin/phpmyadmin
```
4. Crear el contenedor WordPress
  ```bash
docker run -d \
  --name wordpress-wp \
  --network wordpress-net \
  -e WORDPRESS_DB_HOST=mysql-wp:3306 \
  -e WORDPRESS_DB_USER=wpuser \
  -e WORDPRESS_DB_PASSWORD=wppass \
  -e WORDPRESS_DB_NAME=wordpress \
  -v wordpress-vol:/var/www/html \
  -p 8000:80 \
  wordpress:latest
```
Acceso

    WordPress disponible en: http://localhost:8000

    phpMyAdmin disponible en: http://localhost:8080 (usuario: wpuser, contraseña: wppass)

## 7. Conclusiones.
Esta práctica permitió aprender a orquestar varios contenedores Docker para crear un sitio WordPress funcional, gestionando una base de datos MySQL con persistencia de datos mediante volúmenes Docker.
También se comprendió la importancia de las redes Docker para que los contenedores puedan comunicarse internamente.
Además, la implementación de phpMyAdmin facilita la administración visual de la base de datos.
Este entorno se puede eliminar o recrear sin pérdida de datos gracias a los volúmenes, lo que es fundamental para desarrollo y pruebas.
## 8. Imagenes 
### Sitio de Wordpress
![imagen](https://github.com/user-attachments/assets/befe90b1-1902-4348-8ae9-f15f930daeb2)

### Configuración
![Captura de pantalla_20250517_171116](https://github.com/user-attachments/assets/89964ba6-458a-48de-8cae-c3ef5056f204)
![Captura de pantalla_20250517_171048](https://github.com/user-attachments/assets/7296aca8-dc27-48b3-96b6-9037a3f5c81b)

## 9. Audio .
https://drive.google.com/file/d/1dtmv19Evfv2SGIL-SfEBd2J16OAGbmUj/view?usp=sharing 
