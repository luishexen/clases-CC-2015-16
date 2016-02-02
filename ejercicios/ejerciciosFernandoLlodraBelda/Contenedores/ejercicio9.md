## Ejercicio 9

### Instalar a partir de docker una imagen alternativa de Ubuntu y alguna adicional, por ejemplo de CentOS.

Con el comando `$ docker run -it ubuntu bash` instalaremos una imagen Ubuntu a partir de Docker.

![ubuntuByDocker](https://dl.dropboxusercontent.com/s/y1oakfoju8g9xib/Captura%20de%20pantalla%202016-01-28%2020.29.28.png)

### Buscar e instalar una imagen que incluya MongoDB.

Si entramos al **Docker Hub** y buscamos una imagen de Ubuntu con MongoDB instalado ya, encontramos un repositorio 
docker con lo que queremos de un tal **mattselph*.

El comando para bajar e instalar dicha imagen es `$ docker pull mattselph/ubuntu-mongodb` . Con esto, haremos un pull de 
el repositorio de éste usuario, el cual tiene la imagen de Ubuntu con MongoDB.

