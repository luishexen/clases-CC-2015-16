##Comprobar qué interfaces puente se han creado y explicarlos.
Comprobar que lxc funciona correctamente

![imagen_Ejercicio_2](https://dl.dropboxusercontent.com/s/wvq7y7vg99gw5cr/Ejer2_imagen_1.png?dl=0)

Debemos de crear u contenedor en este caso lo llamaramos una-caja.

``` sh
$sudo lxc-create -t ubuntu -n una-caja
```

![imagen_Ejercicio_2_a](https://dl.dropboxusercontent.com/s/amz36opho0on1hx/Ejer2_imagen_2.png?dl=0)

Ejecutamos el contenedor

```sh
$sudo lxc-start una-caja -d
```

![imagen_Ejercicio_2_b](https://dl.dropboxusercontent.com/s/d6lbyr0gpiog38b/Ejer2_imagen_3.png?dl=0)

Lanzamos ipconfig y podemos ver que se han creado 2 interfaces de red  como son eth0 y lo, estas interface virtuales sirven para darle red a los contenedores siempre controlado en todo momento por el root creador del contenedor, esto nos permite tener un control absoluto sobre los contenedores.

```sh
$ubuntu@una-caja:~$ ipconfig
```

![imagen_Ejercicio_2_c](https://dl.dropboxusercontent.com/s/3k1icxny2ssdzmm/Ejer2_imagen_4.png?dl=0)


