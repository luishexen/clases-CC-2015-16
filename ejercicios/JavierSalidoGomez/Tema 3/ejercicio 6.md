## Ejercicio 6: Instalar juju. Usándolo, instalar MySQL en un táper.

Para instalar juju en local usamos el comando:

    sudo apt-get install juju-local

Para arrancar juju usamos el comando:

    juju init
    
Y se crea el archivo .juju/environments.yaml. , el cual debemos abrir y modificar en la línea que pone  "default: amazon" por "default:local"

![](http://googledrive.com/host/0ByKPAGLB_FgcU1E3LVk2dWxsVzA/3-6-1.png)

Indicamos que vamos a trabajar en el entorno local con el comando:

    juju switch local
    
Usamos el comando "juju bootstrap" para crear el táper propio de juju
    
![](http://googledrive.com/host/0ByKPAGLB_FgcU1E3LVk2dWxsVzA/3-6-2.png)

Y finalmente instalamos MySQL con el comando:

    juju deploy mysql
    
Comprobando la correcta instalación con el comando:

    juju status