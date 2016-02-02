## Ejercicio 4:Instalar lxc-webpanel y usarlo para arrancar, parar y visualizar las máquinas virtuales que se tengan instaladas. Desde el panel restringir los recursos que pueden usar: CPU shares, CPUs que se pueden usar (en sistemas multinúcleo) o cantidad de memoria.

Para instalar lxc-webpanel usamos el comando:

    wget https://lxc-webpanel.github.io/tools/install.sh -O - | bash
    
O de forma manual:
   
1. Clonando el repositorio  

    git clone https://github.com/lxc-webpanel/LXC-Web-Panel.git

2. Instalando flask

    pip install flask==0.9

3. Ejecutando lxc-webpanel

    python lwp.py
    
Seguidamente vamos a http://localhost:5000/ y nos autenticamos con usuario y contraseña "admin"



![](http://googledrive.com/host/0ByKPAGLB_FgcU1E3LVk2dWxsVzA/3-4-1.png)

Y vemos los contenedores y su estado actual:

![](http://googledrive.com/host/0ByKPAGLB_FgcU1E3LVk2dWxsVzA/3-4-2.png)

Finalmente configuramos un contenedor y asignamos los siguientes parámetros como ejemplo:

* Memory limit= 2048MB
* Memory + swap limit= 3000MB
* CPUs=1
* CPU shares=1024

![](http://googledrive.com/host/0ByKPAGLB_FgcU1E3LVk2dWxsVzA/3-4-3.png)




