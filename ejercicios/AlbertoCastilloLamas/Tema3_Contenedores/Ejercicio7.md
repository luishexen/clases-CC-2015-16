# Ejercicio 7
## 1. Destruir toda la configuración creada anteriormente
Eliminamos configuración local creada previamente.

`juju destroy-environment local`

![Ejercico7_1](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio7_1.png)

## 2. Volver a crear la máquina anterior y añadirle mediawiki y una relación entre ellos.
Empecemos de nuevo como lo hicimos anteriormente.

```
juju bootstrap
juju deploy mysql
juju deploy mediawiki
juju add-relation mediawiki:db mysql
```

Damos acceso público 

`juju expose mediawiki`

![Ejercico7_2](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio7_2.png)

Comprobemos que funciona el servicio MediaWiki, acceddamos a su dirección pública.

## 3. Crear un script en shell para reproducir la configuración usada en las máquinas que hagan falta.

![Ejercico7_3](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio7_3.png)