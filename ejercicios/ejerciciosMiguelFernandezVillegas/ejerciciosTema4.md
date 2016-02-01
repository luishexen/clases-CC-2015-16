#QEMU
##Instalar QEMU

Para instalar QEMU usamos el siguiente comando `sudo apt-get install qemu-kvm qemu virt-manager virt-viewer libvirt-bin`

##Bajar una distribución de Linux

Podemos bajarnos una distribución con wget o una imagen ya descargada como es en mi caso.

##Crear un disco virtualizado para QEMU

Creamos el disco virtual usando `qemu-img create -f qcow prueba.img 1G`


##Instalar Linux en dicho disco

Con el sguiente comando instalamos nuestro sistema operativo en la unidad virtual ` qemu-system-x86_64 -hda prueba.img -boot d -cdrom Descargas/dsl-4.11.rc2-syslinux.iso -m 2048`

##Ejecutar la máquina instalada para interaccionar con ella con su interfaz gráfica

Cargamos la imagen conel siguiente comando `qemu-system-x86_64 -hda prueba.img` y observamos como está correctamente instalado

![Instalado](https://gyazo.com/eeed8008e1b3e6ec737b407926070b29.png)

##Ejecutar la máquina instalada sin interfaz gráfica, y entrar usando el cliente VNC

Instalamos el cliente para VNC vinagre.

`sudo apt-get install vinagre`

Lanzamos nuevamente la máquina virtual indicando la etiqueta vnc y el puerto a usar. Por defecto se usa el puerto 5900.

`qemu-system-x86_64 -hda prueba.img vnc :1`

La opción :1 hace referencia al puerto 5901. Usaremos ahora vinagre para conectarnos a la máquina virtual de forma remota.

`vinagre 192.168.122.1:5901`

##Instalar apache2 o nginx y probar que sirve páginas web (acceder desde el host a la IP del servidor virtualizado, bien con URL o con su navegador)

Estando conectados con la máquina procedemos a instalar nginx.

`sudo apt-get install nginx`

Nos conectamos a la IP anterior en el sistema anfitrión para comprobar que se puede acceder al servicio web a través del servidor virtualizado.

#IBM Bluemix

##Crear una cuenta en Bluemix

El registro en Bluemix en en su web, de forma sencilla, rellenar el formulario y ya podemos acceder a la cuenta como se muestra en la siguiente captura:

![Bluemix](https://gyazo.com/dcae417c5976639eb2a2b8a14909f064.png)

##Desplegar una web sencilla

En este caso voy a desplegar en python una aplicación sencilla usada para el desarrollo de las prácticas de CC.
Para comenzar creo una aplicación web y con `./cf push PruebaEjercicio` subo mi programa desde la consola de comando CF

![Bluemix](https://gyazo.com/cbab40405ddbf4504f3bf14850af5fc2.png)


Para acceder a la web seguir el enlace http://pruebaejercicio.eu-gb.mybluemix.net/

Web desplegada 

![Pagina](https://gyazo.com/f0bf22728c39e9cb40cc6882e7d466e3.png)

##Monitorízala durante el tiempo que está en ejecución

Aquí podemos monitorear nuestra aplicación en ejecución

![Comofunciona](https://gyazo.com/f2f95ce457c206650d99952320b40ae5.png)



