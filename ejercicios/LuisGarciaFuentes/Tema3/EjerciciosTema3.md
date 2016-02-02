# Ejercicio 1
## Instala LXC en tu versión de Linux favorita. Normalmente la versión en desarrollo, disponible tanto en [GitHub](http://github.com/lxc/lxc) como en el [sitio web](http://linxcontainers.com/) está bastante más avanzada; para evitar problemas sobre todo con las herramientas que vamos a ver más adelante, conviene que te instales la última versión y si es posible una igual o mayor a la 1.0.

Instalamos la versión de lxc del repositorio:

```
sudo apt-get install lxc
```

# Ejercicio 2
## Comprobar qué interfaces puente se han creado y explicarlos.

Vamos a utilizar el siguiente comando para ver nuestras interfaces puente con el sistema   `brctl`:

```
sudo brctl show
```

![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio2-1.png)

Tenemos la interfaz _lxcbr0_ que es la interfaz puente que crea por defecto LXC y además nos sale docker0 ya que en anteriores clases lo hemos utilizado.

# Ejercicio 3
## 1. Crear y ejecutar un contenedor basado en Debian.

Para crear contenedores se usa `lxc-create`, en este caso vamos a crear un contenedor con un sistema **Debian** en su interior (`-t debian`):

```
sudo lxc-create -n debiancaja -t debian -- -r jessie
```

![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio3-1.png)

## 2. Crear y ejecutar un contenedor basado en otra distribución, tal como Fedora. Nota En general, crear un contenedor basado en tu distribución y otro basado en otra que no sea la tuya. Fedora, al parecer, tiene problemas si estás en Ubuntu 13.04 o superior, así que en tal caso usa cualquier otra distro. Por ejemplo, [Óscar Zafra ha logrado instalar Gentoo usando un script descargado desde su sitio, como indica en este comentario en el issue](https://github.com/IV-GII/GII-2013/issues/87#issuecomment-28639976).

Ahora creamos un contenedor con una distribución **Fedora** (`-t fedora`) con su última versión disponible, la 23 (`-- -R 23`):

```
sudo lxc-create -n fedoracaja -t fedora  -- -R 23
```

![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio3-2.png)

# Ejercicio 4
## 1. Instalar `lxc-webpanel` y usarlo para arrancar, parar y visualizar las máquinas virtuales que se tengan instaladas.

Para instalar `lxc-webpanel` nos basta con introducir la siguiente línea:

```
wget https://lxc-webpanel.github.io/tools/install.sh -O - | sudo bash
```

Una vez descargado e instalado solo tendremos que acceder a la dirección [http://localhost:5000/](http://localhost:5000/) con el nombre de usuario y contraseña **admin**.


## 2. Desde el panel restringir los recursos que pueden usar: CPU shares, CPUs que se pueden usar (en sistemas multinúcleo) o cantidad de memoria.

Para restringir los recursos de un contenedor simplemente tenemos que seleccionarlo del panel de la izquierda y desplazarnos hasta la sección correspondiente. Por ejemplo vamos a hacer las siguientes restricciones en el contenedor en el que hemos instalado Debian anteriormente:
- **Límite de memoria (_memory limit_)**: 1024 MB
- **Límite de memoria + espacio de intercambio (_memoria + swap limit_)**: 2048 MB
- **Número de CPUs a su disposición (_CPUs_)**: 1
- **Porcentaje relativo de tiempo de CPU disponible para las tareas en un cgroup (_CPU Shares_)**: 30

# Ejercicio 5
## Comparar las prestaciones de un servidor web en una jaula y el mismo servidor en un contenedor. Usar nginx. Para hacer esta comparación vamos a crear tanto una jaula como un contenedor que contengan la misma versión de Ubuntu 15.10 (Wily) 64 bits.

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

Para instalar servicios dentro del contenedor, usamos los **charms** (script YAML para realizar tareas comunes) de los que no provee el propio sistema, concretamente el de para instalar **MySQL** (`juju deploy mysql`). Ya instalado comprobamos su estado con `juju status`, donde vemos que aparece la máquina anfitriona (**machine "0"**), el contenedor de juju (**machine "1"**) y como servicio instalado aparece **mysql**. Hsta que el contenedor de juju no esté totalmente preparado no dispondrá de ningún identificador y simplemente aparecerá **"pending"**.

Al par de minutos, la máquina ya será reconocida, apareciendo como un contenedor más si los listados con `sudo lxc-ls --fancy`.

# Ejercicio 7
## 1. Destruir toda la configuración creada anteriormente Si queremos destruir una configuración, lo mejor es usar `juju destroy-environment local` donde **local** es la configuración que queremos destruir, en caso contrario es muy posible que se produzcan errores.

## 2. Volver a crear la máquina anterior y añadirle mediawiki y una relación entre ellos. Debemos volver a crear la configuración que teniamos antes de destruir todo:

# Ejercicio 8
## Instalar docker.

```sh
$ sudo apt-get update  
```

Instalamos el paquete docker.io

```sh
$ sudo apt-get install docker.io  
```

![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio8-1.png)


# Ejercicio 9
## 1. Instalar a partir de docker una imagen alternativa de Ubuntu y alguna adicional, por ejemplo de CentOS.

```sh
 $ docker pull centos
```

![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio9-1.png)


##2.- Buscar e instalar una imagen que incluya MongoDB.
```sh
$ docker pull mongo
```

![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio9-1.png)


# Ejercicio 10
## Crear un usuario propio e instalar nginx en el contenedor creado de esta forma.

Accedemos a la imagen de Ubuntu creada en nuestro docker y abrimos una terminal:

```sh
$ sudo docker run -t -i ubuntu /bin/sh
```
![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio10-1.png)

Creamos un usuario en la imagen:

```sh
$  adduser luisdocker
```
![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio10-2.png)

Instalamos software en la imagen:

```sh
$ sudo apt-get install software-properties-common
```
Añadimos un repositorio:

```sh
$  sudo add-apt-repository ppa:nginx/stable
```
Instalamos el programa pedido **nginx**:

```sh
$  sudo apt-get install nginx
```

![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio10-3.png)

# Ejercicio 11
## Crear a partir del contenedor anterior una imagen persistente con commit. Para crear una imagen persistente a partir de un contenedor necesitaremos mínimo conocer su ID largo, para eso añadimos al comando de lista los contenedores de Docker la opción `-notrunc`. Con este ID además podemos **"inspeccionar"** (opción `inspect`) dichos contenedores para obtener diversa información, como el nombre del host, la imagen cargada, si el contenedor está en funcionaniento o la dirección IP.

# Ejercicio 12
## Crear una imagen con las herramientas necesarias para el proyecto de la asignatura sobre un sistema operativo de tu elección. 

Las herramientas necesarias para el proyecto de la asignatura son básicamente **git** y el instalador de **Node.js**; el resto de dependencias se instalarán desde el propio proyecto. Por lo que el archivo Dockerfile será el siguiente:

```
# Submodulo-Red-social-Analytics 1.0

FROM    ubuntu:latest
MAINTAINER Luis Garcia <luisgarfu@gmail.com> Version: 1.0

# Instalar todos los paquetes necesarios para poder realizar realizar el proyecto de CC
RUN apt-get -y install wget
RUN wget -qO- https://deb.nodesource.com/setup_4.x | sudo bash -
RUN sudo apt-get install -y git nodejs
RUN node -v
RUN git clone https://github.com/luishexen/Submodulo-Red-social-Analytics.git /home/Submodulo-Red-social-Analytics
RUN cd /home/Submodulo-Red-social-Analytics && npm install
```

Docker permite crear una imagen usando un Dockerfile almacenado en un repositorio GitHub. Ahora solo queda crear la imagen:

```
sudo docker build -t luishexen/submodulo_red_social_analytics -no-cache=true github.com/luishexen/Submodulo-Red-social-Analytics
```

![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio12-1.png)

Una vez la imagen ha terminado de crearse, podemos ver como aparece en el listado con el resto de imágenes:

```
docker images
```

![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio12-2.png)

Ahora queda comprobar que la imagen se ha creado correctamente iniciándola y verificando que todo lo indicado se ha instalado:

```
docker run -i -t luishexen/submodulo_red_social_analytics /bin/bash

# git --version
# node --version
# npm --version
# cd /home/Submodulo-Red-social-Analytics
# npm list --depth=0
```

![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio12-3.png)

Lo último que también podemos hacer es compartir la imagen que acabamos de crear, para lo que primero necesitaremos una cuenta en [Docker Hub](https://hub.docker.com/). Después, simplemente nos logueamos y subimos la imagen.

```
docker login
docker push luishexen/submodulo_red_social_analytics
```

![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio12-4.png)

Cuando termine se creara una página de la imagen como [esta](https://hub.docker.com/r/luishexen/submodulo_red_social_analytics).

![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio12-5.png)

Finalmente preparamos el **automaticbuild** para que cuando haya cambios en gitHub también se cambie en el Docker:

![img](https://dl.dropboxusercontent.com/u/31245679/Im%C3%A1genes%20de%20Github/CC-Tema3-Ejercicio12-6.png)


