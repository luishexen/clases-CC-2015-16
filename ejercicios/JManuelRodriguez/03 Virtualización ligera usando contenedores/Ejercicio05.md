[José M. Rodríguez](https://github.com/Jmrodriguez90)

Virtualización ligera, usando contenedores: Ejercicio 5
======================================================================

1. Comparar las prestaciones de un servidor web en una jaula y el mismo servidor en un contenedor. Usar nginx.

--

Para poder instalar nginX, usamos las siguientes líneas de comando:

```
sudo apt-get update
sudo apt-get install nginx
```

Para comprobar que el servicio web de nginX está funcinando, usamos el comando `ip addr show eth0 | grep inet | awk '{ print $2; }' | sed 's/\/.*$//'` que nos devolverá una dirección IP que escribiéndola en el navegador, nos mostrará un mensaje de bienvenida de nginx

Luego de realizar la comparación del servidor web entre la jaula y el contenedor con nginX, nos damos cuenta que el contenedor al depender de una conexión virtual a la máquina, esta le resta velocidad al momento de procesar información, cosa que no pasa con la jaula que tiene una conexión directa a la máquina.
A pesar de este pequeño "problema" tampoco puede declararse como rotunda ganadora a la jaula puesto que ambas herramientas, según nginX, van muy de la mano al momento de realizar la comparación.
