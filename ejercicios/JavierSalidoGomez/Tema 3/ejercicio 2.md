## Ejercicio 2: Comprobar qué interfaces puente se han creado y explicarlos.

Una vez hemos creado el contenedor, lo arrancamos con el comando: 

    sudo lxc-start -n contenedor
    
Y vemos las interfaces puente creadas con el comando:

    sudo brctl show
    
![](http://googledrive.com/host/0ByKPAGLB_FgcU1E3LVk2dWxsVzA/3-2-1.png)


Vemos que hay 2 puentes lxcbr0 y vethDWN15A

lxcbr0: es el puente de red creado automáticamente al instalar lxc
vethDWN15A: es la interfaz asignada a lxcbr0 y permite el acceso a Internet dentro del contenedor
