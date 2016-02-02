**Instalar QEMU**

Para instalar la herramienta de virtualización QEMU, con sus componentes adicionales como las herramientas **virt-viewer** y **virt-manager** para gestionar las máquinas creadas mdiante un entorno gráfico, usamos el siguiente comando :

```sudo apt-get install qemu-kvm qemu virt-manager virt-viewer libvirt-bin```

**Bajar una distribución de Linux (p.ej. Debian )**


Nos descargamos una imagen iso de cualquier distribución útil. Para hacer pruebas son recomendables distribuciones de muy reducido peso como :

* [Damn Small Linux](http://distro.ibiblio.org/damnsmall/release_candidate/)
* [SliTaz](http://www.slitaz.org/en/get/)

Estos sistemas operativos basados en Linux ocupan cerca de 50 MB.

**Crear un disco virtualizado para QEMU**

Para crear los discos dondse se van a instlar los sistemas operativos propuestos usamos el siguiente comando :
 
```qemu-img create -f qcow2 <nombre_fichero> <tamanio_fichero>```

Por ejemplo :

```qemu-img create -f qcow2 slitaz.qcow2 1G```

**Instalar Linux en dicho disco**

Creado el disco anterior y descargada la imagen iso ( la última versión de [SliTaz](http://www.slitaz.org/en/news/#d20150520) ) podemos proceder a instalarlo mediante **qemu-system**, es fundamental tener en cuenta la arquitectura que se está usando. Al ser de 64 bits en este caso :

```qemu-system-x86_64 -hda slitaz.qcow2 -boot -d -cdrom slitaz-5.0-rc3.iso -m 1G ```

**Ejecutar la máquina instalada para interaccionar con ella con su interfaz gráfica**

Cargamos la máquina :

```qemu-system-x86_64 -hda slitaz.qcow2```

![imagen](https://i.gyazo.com/1cb655643d0702eff146e2c2e466b36d.png)
> Figura 1. Interfaz gráfica de SliTaz mediante QEMU.

**Ejecutar la máquina instalada sin interfaz gráfica, y entrar usando un cliente VNC.**

Instalamos el cliente para VNC vinagre.

```sudo apt-get install vinagre```

Lanzamos nuevamente la máquina virtual indicando la etiqueta **vnc** y el puerto a usar. Por defecto se usa el puerto 5900. 

```qemu-system-x86_64 -hda slitaz.qcow2 vnc :1```

La opción :1 hace referencia al puerto 5901. Usaremos ahora vinagre para conectarnos a la máquina virutal de forma remota.

```vinagre 192.168.122.1:5901```

**Instalar apache2 o nginx y probar que sirve páginas web (acceder desde el host a la IP del servidor virtualizado, bien con URL o con su navegador)**

Estando conectados con la máquina procedemos a instalar nginx.

```sudo apt-get install nginx```

Nos conectamos a la IP anterior en el sistema anfitrión para comprobar que se puede acceder al servicio web a través del servidor virtualizado.









