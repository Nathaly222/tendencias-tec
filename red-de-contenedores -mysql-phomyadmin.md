## 1. Titulo
Red de contenedores mysql y phomyadmin
## 2. Tiempo de duración
15 min 
## 3. Fundamentos:
En esta práctica, utilizamos Docker para crear contenedores que simulan un pequeño ecosistema de servidor de base de datos y cliente de administración web.
MySQL es un sistema gestor de bases de datos relacional muy utilizado.
phpMyAdmin es una herramienta web que facilita la gestión de bases de datos MySQL.
Docker Network permite que contenedores diferentes se comuniquen entre sí, como si estuvieran en la misma red privada.

Entender estos conceptos es esencial para construir entornos de desarrollo y producción modernos y eficientes.
## 4. Objetivos
### Objetivo general:
Crear un contenedor de phpMyAdmin que se comunique con MySQL.
### Objetivos especificos:
1. Configurar una red personalizada en Docker para conectar ambos contenedores.
2. Comprobar el acceso y la gestión de bases de datos a través de phpMyAdmin.
3. Entender el flujo de creación, conexión y administración de contenedores en un entorno real.
## 5. Repaso 
Aprendimos a crear contenedores de bases de datos como MySQL dentro de Docker.
Entendimos cómo usar variables de entorno para configurar usuarios, contraseñas y bases de datos al momento de crear los contenedores.
Usamos phpMyAdmin, una herramienta gráfica, para conectarnos de manera más amigable a la base de datos.
Descubrimos cómo crear redes personalizadas en Docker para permitir que varios contenedores se comuniquen entre sí de forma segura.
Aprendimos a gestionar bases de datos (crear, modificar, eliminar) desde la interfaz web de phpMyAdmin.
Además, solucionamos errores como conflictos de puertos y configuraciones de red.

## 6. Paso a Paso
1.  Crear una red personalizada
   ```bash
sudo docker network create mynetwork
```
2.  Crear el contenedor de MySQL:
   ```bash
sudo docker run --name mysql_container --network mynetwork -e MYSQL_ROOT_PASSWORD=admin123 -e MYSQL_DATABASE=testdb -p 3306:3306 -d mysql:latest
```
Parámetros usados:

    MYSQL_ROOT_PASSWORD=admin123 define la contraseña de root.

    MYSQL_DATABASE=testdb crea automáticamente una base de datos inicial llamada testdb.
3. Crear el contenedor de phpMyAdmin:
```bash
sudo docker run --name phpmyadmin_container --network mynetwork -e PMA_HOST=mysql_container -p 8081:80 -d phpmyadmin/phpmyadmin
```
Parámetros usados:

    PMA_HOST=mysql_container indica a phpMyAdmin a qué contenedor conectarse.
    
4.  Acceder a phpMyAdmin:
  ```bash
http://localhost:8081
```
e iniciamos sesión:

    Usuario: root

    Contraseña: admin123
5.  Crear una base de datos de prueba:
 Desde la interfaz de phpMyAdmin:

    Click en Nueva base de datos.

    Nombre: users.

    Crear.
## 7. Conclusiones.
Esta práctica fue muy útil para entender cómo levantar servicios básicos de bases de datos y administrarlos fácilmente mediante Docker.
Aprendí a:
Crear redes en Docker.
Hacer que contenedores se comuniquen.
Usar herramientas gráficas para gestionar bases de datos MySQL.
Resolver problemas como puertos ocupados.
Organizar proyectos usando contenedores separados pero conectados.
## 8. Imagenes 
![Captura de pantalla_20250426_142419-1](https://github.com/user-attachments/assets/82841d0f-e857-4be0-99b4-590d2539e2a5)
![Captura de pantalla_20250426_142404](https://github.com/user-attachments/assets/f5fd987e-162c-4e71-9f2c-a5951f644fd5)
![Captura de pantalla_20250426_142242](https://github.com/user-attachments/assets/b17e0679-f361-4808-926d-e9e0c66e46d7)
## 9. Audio .
