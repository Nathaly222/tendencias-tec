# Practica servidor web
## 1. Titulo
Crear y personalizar dos servidores web con Nginx usando Docker
## 2. Tiempo de duración
45 min 
## 3. Fundamentos:
Docker es una plataforma que permite desarrollar, enviar y ejecutar aplicaciones dentro de contenedores, que son entornos ligeros, portables y autosuficientes.

Nginx es un servidor web de alto rendimiento que puede actuar como servidor HTTP, proxy inverso y balanceador de carga. Su eficiencia lo convierte en 
una opción popular para el alojamiento de sitios web estáticos y dinámicos.

Al combinar Docker con Nginx, es posible ejecutar múltiples servidores web en paralelo sin interferencias entre sí, gracias al aislamiento proporcionado por los contenedores.
## 4. Objetivos
### Objetivo general:
Desplegar dos contenedores independientes usando la imagen de Nginx.
### Objetivos especificos:
1. Personalizar el contenido de cada servidor web mediante la edición del archivo index.html.
2. Entender el uso de los comandos básicos de Docker para manipular contenedores y copiar archivos.
3. Verificar el funcionamiento de ambos sitios web accediendo mediante los puertos expuestos.
## 5. Repaso 
En esta actividad se desplegaron dos servidores web independientes utilizando contenedores Docker basados en la imagen oficial de Nginx. Se personalizó el archivo 
index.html en cada servidor para mostrar contenido diferente: uno con información institucional del instituto y otro con información personal del estudiante. 
Para ello, se crearon contenedores, se copiaron archivos desde y hacia el sistema anfitrión, y se editó 
el contenido con herramientas de texto. Finalmente, se comprobó el funcionamiento de los sitios web accediendo desde el navegador mediante los puertos especificados.
## 6. Paso a Paso
```bash
docker run -d --name nginx1 -p 8089:80 nginx
docker cp nginx1:/usr/share/nginx/html/index.html ./index1.html
vi index1.html
docker cp index1.html nginx1:/usr/share/nginx/html/index.html
```

## 7. Conclusiones.
A través de esta práctica se logró implementar dos servidores web de forma simultánea utilizando contenedores Docker, demostrando la eficiencia del uso 
de contenedores para ambientes aislados. También se reforzó el conocimiento del funcionamiento básico del servidor Nginx y la manipulación de archivos 
HTML dentro de contenedores. Esta actividad es una base sólida para avanzar hacia arquitecturas más complejas con múltiples servicios desplegados en 
contenedores independientes.
## 8. Imagenes 
![Captura de pantalla_20250410_235028](https://github.com/user-attachments/assets/fb7cb4d4-688e-4fa3-bab0-7338f5451e8a)
![Captura de pantalla_20250411_001303](https://github.com/user-attachments/assets/acbe5cfb-a54c-42d8-ac19-b36e8a234455)

