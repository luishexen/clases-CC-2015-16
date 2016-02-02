## Ejercicio 1: Instala LXC en tu versión de Linux favorita. Normalmente la versión en desarrollo, disponible tanto en GitHub como en el sitio web está bastante más avanzada; para evitar problemas sobre todo con las herramientas que vamos a ver más adelante, conviene que te instales la última versión y si es posible una igual o mayor a la 1.0.


En primer lugar instalamos lxc con el comando:

    sudo apt-get install lxc
  
Después comprobamos si el kernel soporta lxc-containers con el comando lxc-checkconfig:

![](http://googledrive.com/host/0ByKPAGLB_FgcU1E3LVk2dWxsVzA/3-1-1.png)

Para asegurarnos que la versión instalada es igual a la 1.0 ejecutamos el comando:

    sudo add-apt-repository ppa:ubuntu-lxc/lxc-git-stable-1.0

Que añade el PPA (personal package archives) con la versión 1.0 a nuestro sistema.


Y ya podemos crear contenedores con el comando: 

    sudo lxc-create -n contenedor -t ubuntu
