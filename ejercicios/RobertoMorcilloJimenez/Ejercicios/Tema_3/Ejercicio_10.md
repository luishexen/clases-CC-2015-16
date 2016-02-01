
##1.- Crear un usuario propio e instalar nginx en el contenedor creado de esta forma.
```sh
$ sudo docker run -t -i ubuntu /bin/sh
```

```sh
$  adduser roberto
```

```sh
$ sudo apt-get install software-properties-common
```

```sh
$  sudo add-apt-repository ppa:nginx/stable
```
```sh
$  sudo apt-get install nginx
```
