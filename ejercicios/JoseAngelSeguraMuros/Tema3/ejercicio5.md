# Ejercicio 5
##Comparar las prestaciones de un servidor web en una jaula y el mismo servidor en un contenedor. Usar nginx.

Tras crear toda la infraestructura necesaria para poder ejecutar nginx y que recibiera peticiones tanto en una jaula como en lxc se procede a ejecutar el comando `ab -n 100000000000 direccionservidor/index.html` varias veces.

Y ya sea porque solo hay uno de cada tipo, o porque la jaula se ejecuta directamente sobre la interfaz de red del host los resultados obtenidos son superiores en esta al contrario de lo que podria suponerse que iba a ocurrir.
