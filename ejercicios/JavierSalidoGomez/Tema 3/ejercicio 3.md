## Ejercicio 3:  

### Crear y ejecutar un contenedor basado en Debian.

Creamos el contenedor para la última versión en Debian 8 "Jessie" con el comando: 

    LANG=C SUITE=jessie MIRROR=http://httpredir.debian.org/debian lxc-create -n debian8 -t debian

O usando este comando:

    sudo lxc-create -n debian8 -t debian -- -r jessie
    
    
Para ejecutarlo:

    sudo lxc-start -n debian8

### Crear y ejecutar un contenedor basado en otra distribución, tal como Fedora. Nota En general, crear un contenedor basado en tu distribución y otro basado en otra que no sea la tuya. Fedora, al parecer, tiene problemas si estás en Ubuntu 13.04 o superior, así que en tal caso usa cualquier otra distro. Por ejemplo, Óscar Zafra ha logrado instalar Gentoo usando un script descargado desde su sitio, como indica en este comentario en el issue.

Usamos el comando:

    sudo lxc-create -n contfedora -t fedora

Para ejecutarlo:

    sudo lxc-start -n debian8


![](http://googledrive.com/host/0ByKPAGLB_FgcU1E3LVk2dWxsVzA/3-3-1.png)
