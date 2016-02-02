# Ejercicio 1
##Instalar QEMU

Para instalarlo:

```
sudo apt-get install qemu-kvm qemu
```

# Ejercicio 2
##Bajar una distribución de Linux

Nos bajamos una distribución desde la página web de Ubuntu por ejemplo para virtualizarla con QEMU en un futuro.

# Ejercicio 3
##Crear un disco virtualizado de QEMU

Primero debemos crear un disco duro virtual que será el que utilizará QEMU de la siguiente manera:

```
qemu-img create -f qcow2 miDisco.img 30G
```

# Ejercicio 4
##Instalar linux en dicho disco

Para instalar nuestro sistema operativo con QEMU usaremos el siguiente comando donde tendremos que especificar la ISO de Ubuntu y el disco duro virtual creado en el ejercicio anterior:

```
qemu-system-x86_64 -hda miDisco.img -boot d -cdrom ./Ubuntu.iso -m 512
```

Como vemos hemos asignado 521MB de memoria RAM

# Ejercicio 5
##Ejecutar la maquina instalada para interaccionar con ella con su interfaz grafica

Para lanzarla usamos el siguiente comando, parecido al anterior solo que más simplificado ya que no necesitamos ISO de arranque:

```
qemu-system-x86_64 -hda miDisco.img -m 512
```

# Ejercicio 6
##Ejecutar la maquina instalada sin interfaz grafica, y usando un cliente VNC


Primero instalamos un cliente VNC:
```
sudo apt-get install vncviewer
```

Despues lanzamos la imagen añadiendo -vnc que significa que no se abre el entorno gráfico ya que vamos a acceder de otra forma con vnc:

```
qemu-system-x86_64 -hda miDisco.img -m 512 -vnc :1
```

Buscamos la IP del sistema emulado con:

```
ifconfig virbr0
```

Finalmente con el sguiente comando ya podremos acceder al entorno gráfico de vncviewer:

```
vncviewer 192.168.122.1:5901
```

# Ejercicio 7
##Instalar apache o nginx y probar que sirve paginas web

Con los siguientes comandos tendremos nginx instalado y corriendo en el sistema emulado:

```
sudo apt-get install nginx
sudo service nginx status
```
Con el segundo comando vemos que funciona correctamente nginx.