# Practica servidor web
## 1. Titulo
Elaborar la estructura de un proyecto angular con comandos linux
## 2. Tiempo de duración
15 min 
## 3. Fundamentos:
El desarrollo de aplicaciones web modernas con Angular requiere una estructura bien organizada del proyecto desde sus primeras etapas. Una forma efectiva de lograr esto es utilizando comandos básicos de Linux para crear manualmente los directorios y archivos iniciales. Esta práctica no solo ayuda a comprender la arquitectura interna de una aplicación Angular, sino que también fortalece las habilidades en el uso del sistema operativo Linux.

En este proceso, se utilizarán comandos como mkdir para crear carpetas, touch para generar archivos vacíos, y otras utilidades del sistema que permiten construir la base del proyecto antes de incorporar el framework Angular propiamente dicho.

Este enfoque puede aplicarse como parte de una actividad educativa para entender cómo Angular organiza sus componentes, servicios, módulos y otros elementos clave en una aplicación web moderna.
## 4. Objetivos
### Objetivo general:
Elaborar la estructura básica de un proyecto Angular utilizando comandos nativos de Linux, sin el uso de Angular CLI, aplicando buenas prácticas de organización de carpetas y archivos necesarios para iniciar un proyecto web moderno.
### Objetivos especificos:
1. Crear una jerarquía de carpetas que incluya las secciones principales del proyecto (src, dist, y public), utilizando un número limitado de comandos para optimizar el proceso de desarrollo inicial.
2. Generar los archivos esenciales del proyecto Angular manualmente, tales como README.md, angular.json, package.json y tsconfig.json, utilizando herramientas nativas de Linux sin necesidad de contenido inicial.
## 5. Repaso 
Angular es un framework de desarrollo web basado en TypeScript que permite crear aplicaciones de una sola página (SPA) con una estructura modular y mantenible. Al iniciar un proyecto, Angular CLI suele encargarse de generar automáticamente la estructura básica; sin embargo, es importante entender cómo se organiza internamente un proyecto Angular.

En esta actividad, se propuso realizar la estructura de carpetas y archivos de un proyecto Angular manualmente, utilizando comandos básicos del sistema operativo Linux. Esto nos ayuda a comprender el papel de cada archivo y carpeta dentro del proyecto y fortalece el dominio de la terminal como herramienta de desarrollo.
## 6. Paso a Paso
```bash
mkdir angular
mkdir dist public src
touch angular.json package.json tsconfig.json README.md
mkdir src/app src/app/components src/assets
touch src/index.html src/main.ts src/styles.css src/favicon.ico
mkdir src/assets/images src/assets/fonts src/assets/styles
touch src/app/app.component.ts src/app/app.component.html src/app/app.component.css src/app/app.module.ts
```
## 7. Conclusiones.
* Mediante el uso de comandos básicos de Linux, es posible estructurar manualmente un proyecto Angular sin necesidad de herramientas automatizadas como Angular CLI.

* Esta práctica refuerza el conocimiento del entorno de trabajo y de la arquitectura típica de proyectos Angular, mejorando la comprensión de cada archivo involucrado.

* Crear estructuras de proyecto desde cero promueve buenas prácticas de organización y fomenta la autonomía del desarrollador al momento de configurar entornos personalizados.
## 8. Imagenes 
![Captura de pantalla_20250405_145723](https://github.com/user-attachments/assets/41b31b7a-b291-4bb1-8024-2a5f038fb81e)
![Captura de pantalla_20250405_152101](https://github.com/user-attachments/assets/7c6721c5-e733-4f18-aa44-fe26f050e0f5)
![Captura de pantalla_20250405_165206](https://github.com/user-attachments/assets/d06c2e30-a8f7-4934-8ec3-f622a4026267)



