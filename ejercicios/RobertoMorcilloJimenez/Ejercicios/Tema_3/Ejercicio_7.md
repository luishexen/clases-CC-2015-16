
##1.-Destruir toda la configuración creada anteriormente

```sh
$ sudo destroy-unit mysql/0
```
```sh
$ sudo destroy-machine 1
```

##2.- Volver a crear la máquina anterior y añadirle mediawiki y una relación entre ellos.

```sh
$ juju deploy wikimedia
```
```sh
$ juju add-relation mediawiki:db mysql 
```

##3.- Crear un script en shell para reproducir la configuración usada en las máquinas que hagan falta.


![imagen_Ejercicio_7_a](https://dl.dropboxusercontent.com/s/rkvclmud3ogxbt9/Ejercicio7_%20imagen_1.png?dl=0)

