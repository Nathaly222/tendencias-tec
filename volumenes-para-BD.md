# Practica servidor web
## 1. Titulo
Crear volúmenes para persistir base de datos
## 2. Tiempo de duración
45 min 
## 3. Fundamentos:
Esta semana trabajamos con contenedores Docker y la gestión de bases de datos PostgreSQL. Aprendimos que Docker permite crear entornos aislados donde podemos instalar 
y correr servicios como bases de datos sin necesidad de instalarlos directamente en el sistema operativo. 
También comprendimos el concepto de persistencia de datos, y cómo los volúmenes en Docker permiten mantener los datos incluso después de eliminar el contenedor.
## 4. Objetivos
### Objetivo general:
Crear y ejecutar contenedores PostgreSQL usando Docker.
### Objetivos especificos:
1. Conectarse a los contenedores desde herramientas gráficas como DataGrip.
2. Comprender la diferencia entre trabajar con y sin volúmenes en Docker.
3. Aprender a manejar la persistencia de datos en entornos de desarrollo.
## 5. Repaso 
Primero, creamos un contenedor de PostgreSQL llamado server_db1 sin volumen. Usamos DataGrip para conectarnos al contenedor, creamos una base de datos test, 
una tabla customer y agregamos un registro. 
Luego eliminamos el contenedor y comprobamos que los datos se perdieron.

Después, creamos un volumen Docker y un nuevo contenedor llamado server_db2, esta vez asociándolo al volumen. Repetimos el proceso de crear la base de datos y la tabla, 
insertamos un dato, eliminamos el contenedor y lo volvimos a crear con el mismo volumen. Esta vez, al reconectarnos desde DataGrip, comprobamos que los datos se mantuvieron.
## 6. Paso a Paso
1.  Creación del contenedor server_db1 sin volumen
   ```bash
sudo docker run --name server_db1 -e POSTGRES_PASSWORD=admin -p 5432:5432 -d postgres
```
2.  Conexión a PostgreSQL con DataGrip
   En DataGrip se creó una nueva Data Source PostgreSQL.

Se configuró con:

    Host: localhost

    Puerto: 5432

    Usuario: postgres

    Contraseña: admin 
3. Creación de la base de datos, tabla y datos
En la consola SQL de DataGrip (Query Console) se ejecutó:
```bash
CREATE DATABASE test;
CREATE TABLE customer (
  id SERIAL PRIMARY KEY,
  fullname VARCHAR(100),
  status VARCHAR(50)
);
INSERT INTO customer (fullname, status) VALUES ('Juan Pérez', 'activo');
```
4. Eliminación del contenedor y verificación de pérdida de datos
Se detuvo y eliminó el contenedor:
  ```bash
sudo docker stop server_db1
sudo docker rm server_db1
```
Se volvió a crear con el mismo nombre: 
  ```bash
sudo docker run --name server_db1 -e POSTGRES_PASSWORD=admin -p 5432:5432 -d postgres
```
Después de conectarse nuevamente con DataGrip, se comprobó que la base de datos test y la tabla customer ya no existían, confirmando que los datos no se conservaron (porque no se usó volumen).
5. Creación del volumen Docker
  ```bash
sudo docker volume create pgdata
```

6. Creación del contenedor server_db2 con volumen
  ```bash
sudo docker run --name server_db2 -e POSTGRES_PASSWORD=admin -p 5433:5432 -v pgdata:/var/lib/postgresql/data -d postgres
```
REPETICIÓN DEL PROCESO
## 7. Conclusiones.
Esta experiencia práctica nos permitió entender mejor cómo Docker aísla servicios, y cómo manejar persistencia de datos correctamente mediante volúmenes. 
Vimos que sin un volumen, los datos se eliminan junto con el contenedor. Con un volumen, los datos se guardan de forma segura incluso si el contenedor se borra. 
Además, aprendimos a usar una herramienta profesional como DataGrip, que facilita la gestión visual de bases de datos.
## 8. Imagenes 
### Con Volumen
![Captura de pantalla_20250420_205340](https://github.com/user-attachments/assets/a1a871d7-9982-42ab-9c15-9e653537067a)
![Captura de pantalla_20250420_205110](https://github.com/user-attachments/assets/94464efd-7b4f-4c27-bd9e-3ef9991da295)

### Sin Volumen
![Captura de pantalla_20250420_203908](https://github.com/user-attachments/assets/b8ec1910-69e2-4943-8ffc-3c137498bfa4)
![Captura de pantalla_20250420_203123](https://github.com/user-attachments/assets/79838b33-f30f-40a7-9b2f-c7b0277029ad)

### Conexion
![Captura de pantalla_20250420_201037](https://github.com/user-attachments/assets/1f684afa-2dcd-40ab-89ea-7376135dc6c5)

## 9. Audio .
