# Práctica: TAS7 - Crear imagen personalizada

## 1. Título  
Generar una imagen Docker a partir de una aplicación React y ejecutarla junto con un backend simulado.

## 2. Tiempo de duración  
60 minutos

## 3. Fundamentos  
Docker permite empaquetar aplicaciones y sus dependencias en contenedores portables que pueden ejecutarse en cualquier entorno.  
En esta práctica contenerizaremos una aplicación frontend desarrollada en React, que se comunica con un backend simulado, usando Docker para facilitar el despliegue.

## 4. Objetivos

### Objetivo general  
Contenerizar una aplicación React y ejecutarla junto con un backend simulado utilizando Docker.

### Objetivos específicos  
1. Clonar y ejecutar la aplicación React localmente.  
2. Clonar y levantar el backend simulado para pruebas.  
3. Crear un `Dockerfile` para la aplicación frontend.  
4. Construir la imagen Docker desde el `Dockerfile`.  
5. Ejecutar la aplicación en un contenedor Docker.  

## 5. Requisitos previos  
- Tener instalado Docker y Git.  
- Tener acceso a internet para clonar repositorios.  

---

## 6. Paso a Paso

### 6.1 Clonar el repositorio frontend
```bash
git clone https://github.com/Daviddotcoms/suda-frontend-s6.git
cd suda-frontend-s6
```
### 6.2 Instalar dependencias y verificar funcionamiento local
```bash
npm install
npm run dev
```
### 6.2 Instalar dependencias y verificar funcionamiento local
```bash
npm install
npm run dev
```
### 6.3 Clonar y levantar el backend simulado
```bash
git clone https://github.com/Daviddotcoms/mockAPI.git
cd mockAPI
npm install
npm start
```
### 6.4 Crear un archivo Dockerfile en la raíz de suda-frontend-s6
```bash
# Dockerfile
FROM node:18 AS build

WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

# Usamos una imagen nginx para servir los archivos estáticos
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```
### 6.6 Construir la imagen Docker
```bash
docker build -t react-frontend-suda .
```
### 6.7 Ejecutar el contenedor
```bash
docker run -d -p 8080:80 --name suda-react-app react-frontend-suda
```
### 6.8 Verificar en el navegador

    Accede a: http://localhost:8080
## 7. Conclusiones.
En esta práctica aprendimos a contenerizar una aplicación React utilizando Docker, creando una imagen a partir de un Dockerfile y sirviéndola con Nginx.
También se levantó un backend simulado que permite a la aplicación frontend funcionar correctamente.
Este proceso permite desplegar proyectos frontend en ambientes homogéneos y listos para producción con facilidad y consistencia.
## 8. Imagenes 

### Docker 
![Captura de pantalla 2025-05-17 192013](https://github.com/user-attachments/assets/9b21e4ac-d849-4ebb-b6f0-a63db7234f88)

### Configuración

![Captura de pantalla 2025-05-17 192036](https://github.com/user-attachments/assets/b91e6a1b-6eb8-4778-8d45-247df0a74988)

## 9. Audio .

https://drive.google.com/file/d/1HK44ovpAosI5ai0uXNu22dE7OI_f1663/view?usp=sharing
