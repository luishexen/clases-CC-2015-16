# Ejercicios
## Instala QEMU

`sudo apt-get install qemu-kvm qemu virt-manager virt-viewer libvirt-bin`

![Ejercico1_1](http://googledrive.com/host/0B5Yam2FWqtZPRjRzV09fQ1N2OHM/Ejercicio1_1.png)


##Bajar una distribución de Linux (p.ej. Debian)

`wget http://cdimage.debian.org/debian-cd/8.3.0/i386/iso-cd/debian-8.3.0-i386-netinst.iso`

![Ejercico1_2](http://googledrive.com/host/0B5Yam2FWqtZPRjRzV09fQ1N2OHM/Ejercicio1_2.png)

Descargo la versión 8.3.0 porque no encontraba el link de la versión proporcionado.


##Crear un disco virtualizado para QEMU

`qemu-img create -f qcow2 debian_Prueba1.img 4G`

![Ejercico1_3](http://googledrive.com/host/0B5Yam2FWqtZPRjRzV09fQ1N2OHM/Ejercicio1_3.png)


##Instalar Linux en dicho disco

`qemu-system-x86_64 -hda debian_Prueba1.img -boot d -cdrom ./******** -m 640`

En mi caso estaba bajándome la imagen desde la URL a 20kb/s con una esperanza de que tardara unas 4h, hasta que me descargué la versión subida, por lo que este paso no lo realizo y salto al siguiente.


##Ejecutar la máquina instalada para interaccionar con ella con su interfaz gŕafica

`qemu-system-x86_64 -hda debian_Prueba1.img`


##Ejecutar la máquina instalada sin interfaz gráfica, y entrar usando un cliente VNC

Para ejecutar una máquina sin interfaz gráfica necesitamos instalar un cliente VNC por ejemplo mediante el Centro de Software de Ubuntu.

A continuación podemos ejecutar la máquina sin interfaz

`sudo qemu-system-x86_64 -hda ./public_html/debian_Prueba1.img -vnc :1`

Para conectarnos a ella a través de VNC usaremos

`vncviewer <IP_machine>`

##Instalar Apache2 o nginx y probar que sirve páginas web (acceder desde el host a la IP del servidor virtualizado, bien con cURL o con un navegador)

Para la instalación de apache usamos

`sudo apt-get install apache2`

Y accediendo desde un navegador con la IP adecuada, la de la máquina, obtenemos la prueba de que funciona