**Instalar lxc-webpanel y usarlo para arrancar, parar y visualizar las máquinas virtuales que se tengan instaladas.**

Descargamos e instalamos la última versión de lxc-webpanel ( en modo root ) :

```
wget http://lxc-webpanel.github.io/tools/install.sh -O - |  bash
```

![imagen1](https://i.gyazo.com/56d908fe7fc56a2d4436dd50828d577c.png)
> Figura 1. Instalación de lxc-webpanel

Entrando a través de ```localhost:5000``` mediante un navegador web podemos acceder al panel de control. Una vez logeados podemos gestionar los contenedores creados ( usuario y contraseñan son 'admin' ).

![imagen2](https://i.gyazo.com/d0bfab3b6e21e85c3b40d6795b87b026.png)
> FIgura 2. Panel de control web LXC.


**Desde el panel restringir los recursos que pueden usar: CPU shares, CPUs que se pueden usar (en sistemas multinúcleo) o cantidad de memoria.**

Tras elegir el contenedor creado podemos restringirle los recursos. En este ejemplo reduciremos la cantidad de memoria de 512 MB.

![imagen3](https://i.gyazo.com/33aad7aa08d886313ffab93bc8c662ac.png)
> Figura 13. Restringiendo recursos del contenedor.


