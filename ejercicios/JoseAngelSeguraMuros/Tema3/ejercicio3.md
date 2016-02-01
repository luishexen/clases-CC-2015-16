# Ejercicio 3
##Crear y ejecutar un contenedor basado en Debian.

Para crear el contenedor no hace falta mas que usar el comando sudo `lxc-create -t debian -n debian`

##Crear y ejecutar un contenedor basado en otra distribución, tal como Fedora. 

Para crear el contenedor no hace falta mas que usar el comando sudo `lxc-create -t debian -n debian` A la hora de la instalación salieron un par de problemas relacionados con paquetes sin instalar, estos paquetes eran curl y yum. Se solucionó rapidamente mediante apt-get. 
