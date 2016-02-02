# Ejercicio 10
## Crear un usuario propio e instalar nginx en el contenedor creado de esta forma.

Accedemos, por ejemplo, a la imagen de Ubuntu mediante

`sudo docker run -i -t ubuntu /bin/bash`

Ya dentro vamos a crear un usuario y configurarlo como administrador para tener acceso a cualquier tarea.

```
useradd -d /home/usrdocker -m usrdocker
passwd usrdocker
adduser usrdocker sudo
login usrdocker
```

![Ejercico10_1](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio10_1.png)

Instalamos nginx

```
sudo apt-get install nginx
```

![Ejercico10_2](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio10_2.png)