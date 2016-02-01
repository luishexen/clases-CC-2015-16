[José M. Rodríguez](https://github.com/Jmrodriguez90)

Virtualización ligera, usando contenedores: Ejercicio 10
======================================================================

1. Crear un usuario propio e instalar nginx en el contenedor creado de esta forma.

--

* Agregamos a la ejecución de Docker un terminal de la siguiente manera: `docker run -i -t ubuntu /bin/bash`

* Creamos el usuario dentro de Docker: `adduser jmanuelrodriguez`

* Instalamos nginX:
```
apt-get update
apt-get install nginx
```

* Arrancamos el nginX en Docker: `service nginx start`
