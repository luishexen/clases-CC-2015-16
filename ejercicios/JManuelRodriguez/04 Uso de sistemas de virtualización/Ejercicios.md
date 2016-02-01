[José M. Rodríguez](https://github.com/Jmrodriguez90)

Uso de sistemas de virtualización: Ejercicios
======================================================================

**Instalar QEmu**

--

*Para instalar qemu, usamos el siguiente comando*

`sudo apt-get install qemu-kvm qemu virt-manager virt-viewer libvirt-bin`


====


**Bajar un distro de Linux**

--

*Para efectos de ejercicio, usaré el slitaz que ocupa muy poco espacio*

`wget http://mirror.slitaz.org/iso/4.0/slitaz-4.0.iso`


===


**Crear un disco virtualizado para QEmu**

--

*Creamos un disco duro virtual con el siguiente comando:*

`qemu-img create -f qcow2 slitaz.img 0.5G`


===


**Instalar Linux en dicho disco**

--

*Instalamos Linux con el siguiente comando:*

`qemu-system-x86_64 -hda slitaz.img -boot d -cdrom slitaz-4.0.iso -m 640`


===


**Ejecutar la máquina instalada para interaccionar con ella con su interfaz gráfica**

--

*Ejecuamos la máquina con el siguiente comando:*

`qemu-system-x86_64 -hda slitaz.img`


===


**Ejecutar la máquina instalada sin interfaz gráfica, y entrar usando un cliente VNC**

--

*Instalamos el Visor de Escritorios Remotos desde el centro de Software de Ubuntu*

*Al tener listo el VNC, desde un terminal lanzamos este código*

`qemu-system-x86_64 -hda slitaz.img -vnc :1`

*Y desde otro terminal:*

`vncviewer 192.168.126.4:5901`

*para poder ver la máquina en ejecución*


===


**Crear una cuenta en BlueMix**

--

*Cuenta creada en blueMix con el nick jmrodriguez90*


===


**Desplegar una aplicación web sencilla usando el lenguaje que se desee**

--

*Se creó la app CCACOES usando java como lenguaje*


===


**Modifica y actualiza tu aplicación**

--

**


===


**Monitoriza tu aplicación durante el tiempo que está en ejecución**

--

**
