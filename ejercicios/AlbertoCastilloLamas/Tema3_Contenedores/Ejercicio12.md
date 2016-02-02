# Ejercicio 12
## Crear una imagen con las herramientas necesarias para el proyecto de la asignatura sobre un sistema operativo de tu elección.

Para desplegar nuestra aplicación solo vamos a necesitar git, donde se encuentra nuestra aplicación, además de las herramientas y tecnologías necesarias instaladas automáticamente por la aplicación, solo necesitamos NodeJs para ello.

![Ejercico12_1](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio12_1.png)

A continuación vamos a crear un repositorio específico para Docker ya que permite la creación de imágenes a través de unrepositorio Github lo que nos da movilidad y flexibilidad ante cambios, vamos a ello.

[DockerRepository](https://github.com/alcasla/ProyectoCloudComputing-Docker)

Ahora creemos la imagen.

`docker build -t alcasla/ProyectoCloudComputing-Docker -no-cache=true github.com/alcasla/ProyectoCloudComputing-Docker`

![Ejercico12_2](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio12_2.png)

Ya tenemos la imagen creada, en mi caso lo he hecho dos veces y no le pone nombre a la imagen, nose porqué.

![Ejercico12_3](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio12_3.png)