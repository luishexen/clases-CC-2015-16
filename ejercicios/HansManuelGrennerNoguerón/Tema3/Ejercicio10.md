**Crear un usuario propio e instalar nginx en el contenedor creado de esta forma.**

Usamos la imagen de Centos creada en el paso anterior. Creamos el usuario y lo añadimos al sistema :

```
useradd enpi
passwd enpi
adduser enpi
login enpi
```

A continuación procedemos a instalar nginx ( tenemos que instalar antes EPEL que incluye las últimas versiones al repositorio de nginx ) :

```
yum install epel-release
yum install nginx
```

![imagen](https://i.gyazo.com/5d214b4e42836f81d811b434934d3ba7.png)
> Figura 1. Instalando nginx en el contenedor.
