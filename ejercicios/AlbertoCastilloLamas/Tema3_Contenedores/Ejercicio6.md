# Ejercicio 6
## 1. Instalar `juju`.

```
sudo apt-get install juju-local
```

![Ejercico6_1](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio6_1.png)

## 2. Usándolo, instalar `MySQL` en un táper.
Para ello primero lo iniciamos

`juju init`

![Ejercico6_2](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio6_2.png)

Configuración por defecto para trabajar con servidor Amazon cambiamos para local.

![Ejercico6_3](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio6_3.png)

```
juju switch local
juju bootstrap
```

![Ejercico6_4](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio6_4.png)

Ya está listo para desplegar MySQL

`juju deploy mysql`

![Ejercico6_5](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio6_5.png)
![Ejercico6_6](http://googledrive.com/host/0B5Yam2FWqtZPZGJWT1JHNzI1Uzg/Ejercicio6_6.png)