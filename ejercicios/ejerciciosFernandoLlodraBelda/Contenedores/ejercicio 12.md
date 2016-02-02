## Ejercicio 12

### Crear una imagen con las herramientas necesarias para el proyecto de la asignatura sobre un sistema operativo de tu elección.

Para crear el entorno de pruebas se usa **Docker** y en concreto un Dockerfile donde se describe tanto el sistema operativo que 
tendrá el contenedor como las herramientas que se van a instalar.

Docker tiene una serie de ventajas las cuales podrían resumirse en las siguientes:

- **La portabilidad**: Se puede desplegar el contenedor Docker en cualquier otro sistema, lo que supone un ahorro de tiempo 
a la hora de configurar dicho sistema ya que no se tendría que perder tiempo instalando una a una aquellas herramientas que se necesiten.

- **La Ligereza**: Docker es un sistema de virtualización ligera. Esto quiere decir que virtualizar un sistema operativo con una serie de 
herramientas va a ser mucho menos pesado que si lo hicieramos con un metodo convencional, como por ejemplo, con **VirtualBox**.
Además, con Docker sólo se instalan aquella librerías, configuraciones y archivos que son necesarios.

- **Propio VCS o Sistema de control de versiones**: Docker provee de su propio VCS para tener un control sobre las versiones del contenedor.
Como sucede en Git, se pueden crear repositorios. Ademas su integración con GitHub permite vincular un contenedor con cualquier repositorio que 
se tenga en GitHub.

Para configurar un contenedor Docker se siguen las siguientes pautas:

El primer paso es crearse una cuenta en Docker y a continuación sincronizarla con una cuenta de **GitHub**.

![dockerGit](https://dl.dropboxusercontent.com/s/u5w29xwtypd7cbm/Captura%20de%20pantalla%202016-01-31%2023.44.15.png)

A partir de entonces, cada vez que se haga un push al repositorio de GitHub, se actualizará el repositorio de Docker.
Para comprobar que se ha construido bien la imagen, se puede ver un log de éstas. En la siguiente imagen se puede apreciar.

![logDocker](https://dl.dropboxusercontent.com/s/yue2zrf69o0d3u0/Captura%20de%20pantalla%202016-01-31%2023.46.39.png)

[**Repositorio Docker**](https://hub.docker.com/r/flbkernel/gescochat/)

Para descargar en un contenedor la imagen creada, se ejecuta la orden `$ docker pull flbkernel/gescochat`.

Una vez hecho el pull, se dispondrá de la imagen funcionando en el contenedor correctamente. Esto ha sido posible gracias al 
[**Dockerfile**](https://github.com/Gescosolution/GescoChat/blob/master/Dockerfile) de la aplicación.

![pulled](https://dl.dropboxusercontent.com/s/dxumakzwi8z21w9/Captura%20de%20pantalla%202016-02-01%2000.28.13.png)







