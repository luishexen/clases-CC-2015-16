[José M. Rodríguez](https://github.com/Jmrodriguez90)

Virtualización ligera, usando contenedores: Ejercicio 2
======================================================================
Comprobar qué interfaces puente se han creado y explicarlos.
--

Para comprobar las interfaces, usé el comando ifconfig que arrojó la siguiente información:

1. eth0:   Esta es la conexión común de red.
2. l0:     Esta también es una conexión común de red.
3. lxcbr0: Esta conexión es el enlace entre el contenedor y el sistema.
