# Ejercicio 1
## Instala LXC en tu versión de Linux favorita. Normalmente la versión en desarrollo, disponible tanto en [GitHub](http://github.com/lxc/lxc) como en el [sitio web](http://linxcontainers.com/) está bastante más avanzada; para evitar problemas sobre todo con las herramientas que vamos a ver más adelante, conviene que te instales la última versión y si es posible una igual o mayor a la 1.0.

Instalamos la versión de lxc del repositorio.

```
sudo apt-get install lxc
```

# Ejercicio 2
## Comprobar qué interfaces puente se han creado y explicarlos.

Para conocer los interfaces puente en nuestro sistema usamos 'brctl':

```
sudo brctl show
```

![imagen1](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker1.png)

En mi caso tengo además de la interfaz de lxc la interfaz de docker porque anteriormente estuve probando docker en mi ordenador.

# Ejercicio 3
## 1. Crear y ejecutar un contenedor basado en Debian.
Para crear contenedores se usa `lxc-create`, en este caso vamos a crear un contenedor con un sistema **Debian**.
```
sudo lxc-create -n debiancaja -t debian -- -r jessie
```

![imagen2](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker2.png)

## 2. Crear y ejecutar un contenedor basado en otra distribución, tal como Fedora. Nota En general, crear un contenedor basado en tu distribución y otro basado en otra que no sea la tuya. Fedora, al parecer, tiene problemas si estás en Ubuntu 13.04 o superior, así que en tal caso usa cualquier otra distro. Por ejemplo, [Óscar Zafra ha logrado instalar Gentoo usando un script descargado desde su sitio, como indica en este comentario en el issue](https://github.com/IV-GII/GII-2013/issues/87#issuecomment-28639976).
Ahora creamos un contenedor con una distribución **Fedora**.

```
sudo lxc-create -n fedoracaja -t fedora  -- -R 23
```

![imagen3](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker3.png)


# Ejercicio 4
## 1. Instalar `lxc-webpanel` y usarlo para arrancar, parar y visualizar las máquinas virtuales que se tengan instaladas.
Para instalar `lxc-webpanel` nos basta con introducir la siguiente línea:

```
wget https://lxc-webpanel.github.io/tools/install.sh -O - | sudo bash
```

Una vez descargado e instalado solo tendremos que acceder a la dirección [http://localhost:5000/](http://localhost:5000/) con el nombre de usuario y contraseña **admin**.


## 2. Desde el panel restringir los recursos que pueden usar: CPU shares, CPUs que se pueden usar (en sistemas multinúcleo) o cantidad de memoria.
Para cambiar los parámeros basta con ajustar las barras de desplazamiento:
- **Límite de memoria (_memory limit_)**: 1024 MB
- **Límite de memoria + espacio de intercambio (_memoria + swap limit_)**: 2048 MB
- **Número de CPUs a su disposición (_CPUs_)**: 1
- **Porcentaje relativo de tiempo de CPU disponible para las tareas en un cgroup (_CPU Shares_)**: 25


# Ejercicio 5
## Comparar las prestaciones de un servidor web en una jaula y el mismo servidor en un contenedor. Usar nginx.
Para hacer esta comparación vamos a crear tanto una jaula como un contenedor que contengan la misma versión de Ubuntu 15.10 (Wily) 64 bits.

# Ejercicio 6
## 1. Instalar `juju`.
Como vamos a trabajar en local, instalaremos `juju-local`, que además en las últimas versiones integra MongoDB con el paquete `juju-mongodb`.

```
sudo apt-get install juju-local
```


## 2. Usándolo, instalar `MySQL` en un táper.
Para usar **juju**, primero tenemos que inicializarlo con `juju init`, que crea el archivo con la información sobre las entornos de trabajo en `~/.juju/environments.yaml`.


Como vamos a trabajar en local, editamos dicho fichero y buscamos la línea `default: amazon` (configurado por defecto para trabajar con la nube de Amazon), cambiándolo a `default: local` para establecer que por defecto vamos a trabajar localmente, o también lo podemos hacer directamente con `sed -i 's/default: amazon/default: local/g' ~/.juju/environments.yaml`.

Antes de instalar MySQL, establecemos que vamos a trabajar en el entorno de trabajo local (`juju switch local`), como juju solo puede usar un contenedor que el mismo haya creado lo creamos (`juju bootstrap`).


Para instalar servicios dentro del contenedor, usamos los **charms** (script YAML para realizar tareas comunes) de los que no provee el propio sistema, concretamente el de para instalar **MySQL** (`juju deploy mysql`). Ya instalado comprobamos su estado con `juju status`, donde vemos que aparece la máquina anfitriona (**machine "0"**), el contenedor de juju (**machine "1"**) y como servicio instalado aparece **mysql**. Hasta que el contenedor de juju no esté totalmente preparado no dispondrá de ningún identificador y simplemente aparecerá **"pending"**.


Al par de minutos, la máquina ya será reconocida, apareciendo como un contenedor más si los listados con `sudo lxc-ls --fancy`.

# Ejercicio 7
## 1. Destruir toda la configuración creada anteriormente
## 2. Volver a crear la máquina anterior y añadirle mediawiki y una relación entre ellos.

# Ejercicio 8
## Instalar docker.

```sh
$ sudo apt-get update  
```

Instalamos el paquete docker.io

```sh
$ sudo apt-get install docker.io  
```


![imagen4](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker4.png)


# Ejercicio 9

## 1.- Instalar a partir de docker una imagen alternativa de Ubuntu y alguna adicional, por ejemplo de CentOS.
```sh
 $ docker pull centos
```

![imagen5](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker5.png)

##2.- Buscar e instalar una imagen que incluya MongoDB.
```sh
$ docker pull mongo
```

![imagen5](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker5.png)


# Ejercicio 10
## Crear un usuario propio e instalar nginx en el contenedor creado de esta forma.

Entramos en la imagen de ubunto de nuestro docker abriendo la consola:

```sh
$ sudo docker run -t -i ubuntu /bin/sh
```

Creamos el usuario:

```sh
$  adduser alberto
```

![imagen6](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker6.png)

Procedemos a instalar Software en la imagen

```sh
$ sudo apt-get install software-properties-common
```

Añadimos repositorios:

```sh
$  sudo add-apt-repository ppa:nginx/stable
```

Instalamos nginx:

```sh
$  sudo apt-get install nginx
```

![imagen7](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker7.png)


# Ejercicio 11
## Crear a partir del contenedor anterior una imagen persistente con commit.
Para crear una imagen persistente a partir de un contenedor necesitaremos mínimo conocer su ID largo, para eso añadimos al comando de lista los contenedores de Docker la opción `-notrunc`. Con este ID además podemos **"inspeccionar"** (opción `inspect`) dichos contenedores para obtener diversa información, como el nombre del host, la imagen cargada, si el contenedor está en funcionaniento o la dirección IP.


# Ejercicio 12
## Crear una imagen con las herramientas necesarias para el proyecto de la asignatura sobre un sistema operativo de tu elección.

Las herramientas necesarias para el proyecto de la asignatura son básicamente **git** y el instalador de **Node.js**; el resto de dependencias se instalarán desde el propio proyecto. Por lo que el archivo Dockerfile será el siguiente:

```
# Submodulo-Red-social-Juego 1.0

FROM    ubuntu:latest
MAINTAINER Alberto Garcia <albertogarf91@gmail.com> Version: 1.0

# Instalar todos los paquetes necesarios para poder realizar realizar el proyecto de CC
RUN apt-get -y install wget
RUN wget -qO- https://deb.nodesource.com/setup_4.x | sudo bash -
RUN sudo apt-get install -y git nodejs
RUN node -v
RUN git clone https://github.com/albertogarf91/Submodulo-Red-social-Juego.git /home/Submodulo-Red-social-Juego
RUN cd /home/Submodulo-Red-social-Juego && npm install
```

Docker permite crear una imagen usando un Dockerfile almacenado en un repositorio GitHub.

Ahora solo queda crear la imagen:

```
docker build -t albertogarf91/submodulo_red_social_juego -no-cache=true github.com/albertogarf91/Submodulo-Red-social-Juego
```

![imagen8](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker8.png)

Con el siguiente comando vemos las imagenes de nuestro docker y vemos que está la de nuestro proyecto:

```
docker images
```

![imagen9](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker9.png)

Ahora queda comprobar que la imagen se ha creado correctamente iniciándola y verificando que todo lo indicado se ha instalado:

```
docker run -i -t albertogarf91/submodulo_red_social_juego /bin/bash

# git --version
# node --version
# npm --version
# cd /home/Submodulo-Red-social-Juego
# npm list --depth=0
```

![imagen10](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker10.png)

Lo último que también podemos hacer es compartir la imagen que acabamos de crear, para lo que primero necesitaremos una cuenta en [Docker Hub](https://hub.docker.com/). Después, simplemente nos logueamos y subimos la imagen.

```
docker login
docker push albertogarf91/submodulo_red_social_juego
```

![imagen11](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker11.png)

Cuando termine se creara una página de la imagen como [esta](https://hub.docker.com/r/albertogarf91/submodulo_red_social_juego/).

![imagen12](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker12.png)

Finalmente preparamos el automatic build para que cuando haya cambios en Github se actualice en Docker.

Finalmente tenemos este resultado:

![imagen13](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/docker13.png)