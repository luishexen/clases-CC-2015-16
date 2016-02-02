# Instalar QEMU.
Vamos a instalar el emulador QEMU y además unos cuantos paquetes recomendados más:

```
sudo apt-get install qemu-kvm qemu virt-manager virt-viewer libvirt-bin
```

![eje01_img01](https://dl.dropboxusercontent.com/s/pe9c6w1zhn3zq65/eje01_img01.png)

# Bajar una distribución de Linux (p.ej. Debian).
La distribución a descargar es **Lubuntu**, una versión de Ubuntu con el escritorio _LXDE_ que es muy ligero; además, será la versión para arquitecturas de _32 bits_ (i386), para que entre todo luego sea menos pesado emular el sistema.

```
wget http://cdimage.ubuntu.com/lubuntu/releases/15.10/release/lubuntu-15.10-desktop-i386.iso
```

![eje02_img01](https://dl.dropboxusercontent.com/s/r6yb2cpsupg251l/eje02_img01.png)

# Crear un disco virtualizado para QEMU.
Ahora creamos la imagen del disco duro virtual que vamos a usar con el emulador. El formato del disco será **QCOW2** y con una capacidad de **20GB**.

```
qemu-img create -f qcow2 lubuntu.img 20G
```

![eje03_img01](https://dl.dropboxusercontent.com/s/mrvcvg0bju253g7/eje03_img01.png)

# Instalar Linux en dicho disco.
Creamos una máquina virtual en la que instalar la versión de Lubuntu que hemos descargado. Tenemos que indicar que vamos a usar el disco duro virtual que hemos creado en el paso anterior (`lubuntu.img`), la imagen de instalación (`lubuntu-15.10-desktop-i386.iso`) y la cantidad de memoria RAM que le vamos a asignar a la máquina, que serán **2GB** en este caso. Es importante también tener en cuenta que si no activamos **KVM** (`-enable-kvm`) la emulación será mucho más lenta.

```
qemu-system-x86_64 -enable-kvm -hda lubuntu.img -boot d -cdrom lubuntu-15.10-desktop-i386.iso -m 2G -name lubuntu
```

![eje04_img01](https://dl.dropboxusercontent.com/s/ax2cbztcduaersw/eje04_img01.png)

Otra imagen:

![eje04_img02](https://dl.dropboxusercontent.com/s/x9lom98vieassou/eje04_img02.png)

Y otra imagen:

![eje04_img03](https://dl.dropboxusercontent.com/s/668bwuzuw27uafd/eje04_img03.png)

# Ejecutar la máquina instalada para interaccionar con ella con su interfaz gráfica.

Una vez que el sistema está instalado, podremos arrancar la imagen para acceder al interfaz gráfico del sistema.

```
qemu-system-x86_64 -enable-kvm -boot order=c -drive file=lubuntu.img,if=virtio -m 2G -name lubuntu
```

![eje05_img01](https://dl.dropboxusercontent.com/s/02t4fiibnmw8yl6/eje05_img01.png)

Aquí podemos ver el sistema ya arrancado:

![eje05_img02](https://dl.dropboxusercontent.com/s/tqds66tmlqjdueg/eje05_img02.png)

# Ejecutar la máquina instalada sin interfaz gráfica, y entrar usando un cliente VNC.

Para ejecutar la máquina virtual sin interfaz gráfica tenemos que arrancarla dentro de un **servidor VNC** (opción `-vnc :1`). Esta vez no se abrirá ninguna ventana al ejecutar la orden.

```
qemu-system-x86_64 -enable-kvm -boot order=c -drive file=lubuntu.img,if=virtio -m 2G -name lubuntu -vnc :1
```

![eje06_img01](https://dl.dropboxusercontent.com/s/awxz6jx5iik54rv/eje06_img01.png)

Para conectarnos al servidor VNC de la máquina virtual necesitaremos instalar en nuestro sistema local un **cliente VNC** como puede ser **VNC Viewer**, lo que vamos a hacer desde otro terminal.

```
sudo apt-get install vncviewer
```

![eje06_img02](https://dl.dropboxusercontent.com/s/ani8fk3bhhp659c/eje06_img02.png)

También necesitaremos conocer la dirección IP de la máquina virtual, para ello consultamos la información de la interfaz **virbr0**, que es la interfaz NAT por defecto para máquinas de este sistema.

```
ifconfig virbr0
```

![eje06_img03](https://dl.dropboxusercontent.com/s/7fgjnzddjzlkwe7/eje06_img03.png)

Por último, solo nos queda conectarnos a la máquina a través de VNC indicando la IP de la máquina y el puerto de escucha VNC por defecto, **5901**.

```
vncviewer 192.168.122.1:5901
```
![eje06_img04](https://dl.dropboxusercontent.com/s/qczkex4qi13nf2i/eje06_img04.png)

# Instalar Apache2 o nginx y probar que sirve páginas web (acceder desde el host a la IP del servidor virtualizado, bien con cURL o con un navegador).

En esta ocasión desde el interior de la máquina virtual, instalremos **nginx**.

```
sudo apt-get install nginx
```

![eje07_img01](https://dl.dropboxusercontent.com/s/xjfw8k35f397c0y/eje07_img01.png)

Una vez instalado, comprobamos que está funcionando correctamente.


```
sudo service nginx status
```

![eje07_img02](https://dl.dropboxusercontent.com/s/e5jkv5w22mhzwuj/eje07_img02.png)

Por el método que tiene _QEMU_ de gestionar las interconexiones entre sistema locales y virtuales, para que ahora podamos conectarnos desde nuestro sistema al servidor que acabamos de instalar es necesario **redirigir** un puerto en nuestro sistema local a un puerto en el sistema virtual; como es un servidor web, usará el puerto _80_ por defecto, así que vamos a redirigir ese puerto a nuestro puerto local _80_. Esto se hace con la opción `-redir tcp:80::80`, además como el puerto 80 es un puerto reservado del sistema, tendremos que ejecutar la máquina virtual con permisos de **superusuario** en este caso.

```
sudo qemu-system-x86_64 -enable-kvm -boot order=c -drive file=lubuntu.img,if=virtio -m 2G -name lubuntu -redir tcp:80::80
```

![eje07_img03](https://dl.dropboxusercontent.com/s/yy86b0rpe21b56y/eje07_img03.png)
