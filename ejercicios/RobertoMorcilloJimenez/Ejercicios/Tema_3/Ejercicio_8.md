
##1.- Instalar docker.
```sh
$ sudo apt-get update  
```

Instalamos el paquete docker.io

```sh
$ sudo apt-get install docker.io  
```
Creamos un enlace a docker.io para poder usar simplemente docker como comando

```sh
$ sudo ln -sf /usr/bin/docker.io /usr/local/bin/docker  
```
Habilitamos el autocompletado para docker

```sh
$ sudo sed -i '$acomplete -F _docker docker' /etc/bash_completion.d/docker.io 
```
![imagen_Ejercicio_8_a](https://dl.dropboxusercontent.com/s/5uxhbldvpx8fczz/Ejercicio8_imagen_1.png?dl=0)
