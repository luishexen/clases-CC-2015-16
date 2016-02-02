**Comprobar qué interfaces puente se han creado y explicarlos.**

Instalaremos un contenedor usando una imagen de ubuntu-cloud.

```
sudo lxc-create -t ubuntu-cloud -n nubecilla
```

Arrancamos la imagen y entramos a su consola.

```
sudo lxc-start -n nubecilla
sudo lxc-console -n nubecilla
```

![lxc](https://i.gyazo.com/74f891c0e9c173c1c4c5a3066f446f21.png)
> Figura 1. Contenedor de ubuntu-cloud en funcionamiento.

Tras crear mediante lxc un nuevo contenedor se genera una interfaz virutal que permite disponer de una conexión tipo ehternet dentro de un contenedor tanto con el host como con internet. Comprobamos mediante ```ifconfig -a``` , mientras el contenedor está en funcionamiento, los interfaces puente creados.

![interfaces](https://i.gyazo.com/7facb6a18c98ece1d09adaaaaf0839dd.png)
> Figura 2. Interfaces puente creados.
