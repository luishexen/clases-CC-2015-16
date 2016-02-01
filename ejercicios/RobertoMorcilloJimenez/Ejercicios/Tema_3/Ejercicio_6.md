
##1.-Instalar juju.

##Usándolo, instalar MySQL en un táper.

```sh
$ sudo add-apt-repository ppa:juju/stable
```
```sh
$ sudo apt-get update && sudo apt-get install juju-core juju-local
```
```sh
$ juju init (editar el fichero que genera y poner “default: local”)
```
```sh
$ juju switch local
```
```sh
$ sudo apt-get install mongodb-server MongoDB (sino lo tienes instalado)
```
```sh
$ juju bootstrap (que crea el contenedor (juju-agent-robermorji))
```
```sh
$ juju deploy mysql(desplegamos el servicio)
```
```sh
$ juju expose mysql(desplegamos el servicio)
```

![imagen_Ejercicio_6_a](https://dl.dropboxusercontent.com/s/ffwrt242o9sy9at/Ejer6_imagen1.png?dl=0)




