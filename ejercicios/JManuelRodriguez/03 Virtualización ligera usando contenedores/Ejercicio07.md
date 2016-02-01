[José M. Rodríguez](https://github.com/Jmrodriguez90)

Virtualización ligera, usando contenedores: Ejercicio 7
======================================================================

1. Destruir toda la configuración creada anteriormente
2. Volver a crear la máquina anterior y añadirle mediawiki y una relación entre ellos.
3. Crear un script en shell para reproducir la configuración usada en las máquinas que hagan falta.

--

Para cubrir el primer objetivo, debemos seguir los comandos que a continuación se detallan:

- Primero, habrá que destruir las unidades creadas: `sudo juju destroy-unit mysql/0`
- Luego ya podremos desstruir la máquina que creamos: `sudo juju destroy-machine 2` el número 2 indica el número que tiene la máquina creada.

Ahor pasamos a crear nuevamente la máquina: `sudo juju add-machine`, esta se creará con un número posterior al último utilizado.

Instalamos el servicio de MediaWiki: `juju deploy mediawiki` y luego de haberlo instalado, pasamos a desplegarlo: `juju expose mediawiki`
