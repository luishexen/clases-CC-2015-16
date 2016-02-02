#Virtualización QEMU

##Instalación QEMU

Para instalar QEMU usamos el siguiente comando:

    sudo apt-get install qemu-kvm qemu virt-manager virt-viewer libvirt-bin


##Bajar una distribución de Linux

Bajamos cualquiera, en mi caso la más reciente de Debian:

![](http://googledrive.com/host/0ByKPAGLB_FgcU1E3LVk2dWxsVzA/4-1.png)

##Crear un disco virtualizado para QEMU

Lo hacemos a través del comando:

    qemu-img create -f qcow2 debian-8.3.0-amd64-i386-netinst.iso 3G
    




##Instalar linux en dicho disco

Usamos el comando:

    sudo qemu-system-x86_64 -hda debian.img -boot d -cdrom debian-8.3.0-amd64-i386-netinst.iso -m 640
 
![](http://googledrive.com/host/0ByKPAGLB_FgcU1E3LVk2dWxsVzA/4-2.png)

##Ejecutar la máquina instalada para interaccionar con ella con su interfaz gráfica.

Usamos el comando: 

 qemu-system-x86_64 -hda debian.img
 
Siendo debian.img la imagen creada anteriormente

## Ejecutar la máquina instalada sin interfaz gráfica, y entrar usando un cliente VNC.


Para ejecutar la máquina sin interfaz gráfica: 
    sudo qemu-system-x86_64 -hda ./public_html/debian.img -vnc :1

Para acceder a la máquina usaremos el comando:
    vncviewer IP_maquina_virtual

 
##Instalar Apache2 o nginx y probar que sirve páginas web (acceder desde el host a la IP del servidor virtualizado, bien con cURL o con un navegador). 


Primero instalamos nginx dentro de la máquina con el comando que ya conocemos:

    sudo apt-get install nginx
    

En caso de apache usaremos el comando:

    sudo apt-get install apache2
    
    

    
    

    



