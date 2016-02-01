[José M. Rodríguez](https://github.com/Jmrodriguez90)

Virtualización ligera, usando contenedores: Ejercicio 8
======================================================================

1. Instalar docker

--

**Para poder instalar Docker, de tres diferente maneras, seguimos estos pasos:**

**Instalación Docker 1:**

* Tener instalado curl, si lo tenemos, se instala de esta manera:
`sudo apt-get install curl -y `
* Para instalar Docker, este comando:
`curl -sSL https://get.docker.io/ubuntu/ | sudo sh`


**Instalación Docker 2:**

* Instalar soporte https para APT
```
[ -e /usr/lib/apt/methods/https ] || {
  apt-get update
  apt-get install apt-transport-https
 } 
```
* Agregamos la llave del repositorio de Docker al llavero local
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 36A1D7869245C8950F966E92D8576A8BA88D21E9
```
* Añadimos el repositorio a la lista de fuentes de APT (quizá salga una advertencia sobre la confiabilidad del paquete, aceptamos)
```
sudo sh -c "echo deb https://get.docker.io/ubuntu docker main\
 > /etc/apt/sources.list.d/docker.list"
```
* Actualizamos
```
sudo apt-get update
```
* Instalamos el paquete lxc-docker
```
sudo apt-get install lxc-docker
```


**Instalación Docker 3:**

* Actualizamos
```
sudo apt-get update
```
* Instalamos el paquete docker.io
```
sudo apt-get install docker.io
```
* Creamos un enlace a docker.io para poder usar simplemente docker como comando
```
sudo ln -sf /usr/bin/docker.io /usr/local/bin/docker
```
* Habilitamos el autocompletado para docker
```
sudo sed -i '$acomplete -F _docker docker' /etc/bash_completion.d/docker.io
```

*Para este ejercicio, utilizamos la opción número 3 de instalación*


podemos ver la version de docker que instalamos ejecutando con: `docker -v`

Y para probar que realmente este funcionando, podemos ejecutar el siguiente comando:

`sudo docker run -i -t busybox cat --help`

*Hay que esperar unos minutos para que responda.*


