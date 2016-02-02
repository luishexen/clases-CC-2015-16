## Ejercicio 8: Instalar docker.


Primero debemos comprobar la versión de kernel si se va a instalar en Ubuntu, para que sea mayor de la 3.10 y comprobar también que se trata de la versión de 64 bits. Para ello usamos el comando uname -r:

En mi caso se trata de la versión 3.19.0-25-generic, por lo que no habría problema.

Seguidamente hay que añadir una gpg key con el comando:

    sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
    

Una vez hecho esto, nos vamos al archivo /etc/apt/sources.list.d/docker.list (en caso de que no exista lo creamos) y añadimos una entrada en función de la versión de Ubuntu que se tenga. En mi caso se trata de Ubuntu 14.04 y la entrada a añadir es:

    deb https://apt.dockerproject.org/repo ubuntu-trusty main
    
Actualizamos el apt con:

    apt-get update

Purgamos el antiguo apt si existe:

    apt-get purge lxc-docker
    
    
Ya hemos completado la etapa de prerrequisitos, para instalarlo ahora debemos seguir los siguientes pasos:

1. Actualizamos el apt con "sudo apt-get update"

2. Instalamos docker con "sudo apt-get install docker-engine"

3. Arrancamos el demonio con el comando "sudo service docker start"

4. Finalmente probamos que funciona con "sudo docker run hello-world"

Apareciendo el siguiente mensaje:

![](http://googledrive.com/host/0ByKPAGLB_FgcU1E3LVk2dWxsVzA/3-8-1.png)

