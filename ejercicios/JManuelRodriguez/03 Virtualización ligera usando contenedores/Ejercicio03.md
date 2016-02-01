[José M. Rodríguez](https://github.com/Jmrodriguez90)

Virtualización ligera, usando contenedores: Ejercicio 3
======================================================================

1. Crear y ejecutar un contenedor basado en Debian.

2. Crear y ejecutar un contenedor basado en otra distribución, tal como Fedora. Nota en general, crear un contenedor basado en tu distribución y otro basado en otra que no sea la tuya. Fedora, al parecer, tiene problemas si estás en Ubuntu 13.04 o superior, así que en tal caso usa cualquier otra distro.

--

- [x] *Para crear un contenedor con Ubuntu, usamos el siguiente comando:*

`sudo lxc-create -t ubuntu - n Ubuntu1`

- [x] *Para instalar cualquier otra versión, solamente es neceario cambiar el nombre de la distribución ya que están en plantillas que se pueden usar en el momento que se desee.*

`sudo lxc-create -t debian - n Ubuntu1`
