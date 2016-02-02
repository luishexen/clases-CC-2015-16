# Ejercicio 4
## 1. Instalar `lxc-webpanel` y usarlo para arrancar, parar y visualizar las máquinas virtuales que se tengan instaladas.
Para instalar `lxc-webpanel` nos basta con introducir la siguiente línea:

```
wget https://lxc-webpanel.github.io/tools/install.sh -O - | sudo bash
```
![Ejercico4_1](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio4_1.png)

Accedemos a la dirección [localhost](http://localhost:5000/) dando acceso al web panel de LXC.

![Ejercico4_2](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio4_2.png)
![Ejercico4_3](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio4_3.png)

## 2. Desde el panel restringir los recursos que pueden usar: CPU shares, CPUs que se pueden usar (en sistemas multinúcleo) o cantidad de memoria.

Navegando a través del panel lateral a la izquierda nos permite de forma gráfica realizar edición de recursos para los distintos contenedores.

![Ejercico4_4](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio4_4.png)
![Ejercico4_5](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio4_5.png)