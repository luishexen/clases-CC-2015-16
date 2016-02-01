# Ejercicios del Tema 4

### Ejercicios

Para instalar QEMU en Mac OSX es necesario instalar algunos componentes adicionales. En primer lugar es necesario tener instaldo XCode, ya que con el se instalarán los compiladores de GCC necesarios para que la instalación de QEMU compile sus fuentes e instale el software. También es necesario instalar Brew, que no es más que un gestor de paquetes similar a "apt-get", que permite gestionar las instalaciones de nuevo software. De esta forma, lo único que falta para instalar QEMU es ejecutar el comando `brew install qemu`.

Una vez instalado QEMU, vamos a instalar un sistema operativo; en nuestro caso usaremos Debian 8.2.0. Descargamos la imagen de su web y preparamos el espacio necesario para la máquina. Para reservar espacio en disco para poder instalar Debian, necesitaremos ejecutar el comando `qemu-img create -f qcow2 ~/qemu/debian.img 7G`. La parte "7G" indica el tamaño a reservar para el sistema, en este caso 7GB.

Y finalmente usamos `qemu-system-x86_64 -hda ~/qemu/debian.img -cdrom ~/Downloads/debian-8.2.0-i386-netinst.iso` para iniciar la instalación de Debian. En este comando la opción "-hda" sirve para indicar el lugar de nuestro sistema host en el que se guardará. La opción "-cdrom" sirve para indicar la imagen del sistema que vamos a instalar, en este caso, la imagen de Debian.

![](http://i.imgur.com/96SkF4F.png)


Una vez hecho esto, simplemente instalamos Debian como se suele hacer en cualquier máquina.

Una vez acabada la instalación, podemos iniciar nuestra máquina recien creada usando el comando `qemu-system-x86_64 -hda ~/qemu/debian.img`.


Para acceder al servidor web nginx debemos iniciar la máquina virtual con `qemu-system-x86_64 -hda ~/qemu/debian.img -redir tcp:8080::80`, de esta forma nos redirecciona el puerto 80 del sistema virtualizado al puerto 8080 del host. Así podremos entrar desde nuestro sistema host accediendo a la dirección http://localhost:8080/

![](http://i.imgur.com/swTMt1F.png)


En los ejercicios también se pide utilizar VNC para conectarse al sistema y utilizarlo. En mi caso no tengo la posibilidad de hacer esto, pues utilizo Mac OSX y KVM parece que no es compatible con este sistema. De hecho, he tenido que entrar a la máquina virtual una vez instalada a través del modo recuperación (solo texto) y deshabilitar el inicio de la interfaz gráfica para poder iniciar el sistema e instalar nginx. Intenté conectarme por VNC sin iniciar la interfaz gráfica, pero se queda cargando la conexión e intentando iniciar el modo gráfico.
