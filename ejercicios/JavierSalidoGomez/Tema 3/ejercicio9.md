## Ejercicio 9: Instalar a partir de docker una imagen alternativa de Ubuntu y alguna adicional, por ejemplo de CentOS. Buscar e instalar una imagen que incluya MongoDB.


Para ejecutar el demonio de docker en segundo plano usamos el comando:

    sudo docker -d &


Para instalar una imagen alternativa a mi versión de Ubuntu (la 14.04) usaré el comando

    sudo docker pull ubuntu:15.04

Para instalar una imagen de centOS como por ejemplo la versión 7, usamos el comando:

    sudo docker pull centos:7

Finalmente para instalar una imagen de mongoDB usamos el comando:

    sudo docker pull mongo
    
Que por defecto nos encuentra la ultima versión "latest" si no especificamos un tag

Con el comando sudo docker images podemos comprobar las imagenes que hemos instalado, si todo ha ido correctamente:

![](http://googledrive.com/host/0ByKPAGLB_FgcU1E3LVk2dWxsVzA/3-9-1.png)