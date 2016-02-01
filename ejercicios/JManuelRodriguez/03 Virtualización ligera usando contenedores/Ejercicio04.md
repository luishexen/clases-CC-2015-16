[José M. Rodríguez](https://github.com/Jmrodriguez90)

Virtualización ligera, usando contenedores: Ejercicio 4
======================================================================

1. Instalar lxc-webpanel y usarlo para arrancar, parar y visualizar las máquinas virtuales que se tengan instaladas.

2. Desde el panel restringir los recursos que pueden usar: CPU shares, CPUs que se pueden usar (en sistemas multinúcleo) o cantidad de memoria.

--

Para poder realizar la instalación del webpanel, será necesario tener privilegios de súper usuario.

- Instalamos el web panel con la siguiente instrucción:

 - `wget http://lxc-webpanel.github.io/tools/install.sh -O – | bash`

Después de haberse instalado, nos dice que podemos acceder a él, mediante la siguiente direción.
 - `http://your-ip-address:5000/`

En este caso cambiaremos `your-ip-address` por `localhost` y al requerir usuario y contraseña, usaremos admin/admin respectivamente.

Una vez dentro del WebPanel, se puede ver claramente cómo desde la parte gráfica podemos visualizar las máquinas que tenemos instaladas, arrancar cada una de ellas, paralas o congelarlas.


- Para poder configurarlas, usaremos el apartado "Check config" para poder visualizar lo que se puede y no puede hacerce con cada máquina.

