
##1.- Instalar lxc-webpanel y usarlo para arrancar, parar y visualizar las máquinas virtuales que se tengan instaladas.

##2.- Desde el panel restringir los recursos que pueden usar: CPU shares, CPUs que se pueden usar (en sistemas multinúcleo) o cantidad de memoria

Instalamos con el siguiente comando el lxc-panel:

```sh
sudo wget https://lxc-webpanel.github.io/tools/install.sh -O - | sudo bash
```
![imagen_Ejercicio_4_a](https://dl.dropboxusercontent.com/s/ilcp6kf0cx71uit/Ejer4_imagen1.png?dl=0)

![imagen_Ejercicio_4_b](https://dl.dropboxusercontent.com/s/yln5qkx4qt4gogi/Ejer4_imagen_2.png?dl=0)

Restringuimos los distintos recursos que vamos a utilizar:

![imagen_Ejercicio_4_c](https://dl.dropboxusercontent.com/s/vv6tlsd7rm421au/Ejer4_imagen_3.png?dl=0)

Ejecutamos apply.
