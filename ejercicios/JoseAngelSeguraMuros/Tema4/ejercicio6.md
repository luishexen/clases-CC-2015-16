# Ejercicio 6
##Ejecutar la maquina instalada sin interfaz grafica, y usando un cliente VNC

Primero instalaremos un cliente VNC, si usamos ubuntu la forma más simple de hacerlo es mediante `apt-get install` o directamente desde el centro de software.

Despues lanzamos la imagen como siempre: `qemu-system-x86_64 -hda nombre_disco.img -m 640 -vnc :1` el flag -vnc le indica a QEMU que lance la imagen sin interfaz y con vnc activado.

Por ultimo desde una segunda terminal lanzamos el cliente vnc indicandole la dirección IP del contenedor corriendo, y estaremos dentro.