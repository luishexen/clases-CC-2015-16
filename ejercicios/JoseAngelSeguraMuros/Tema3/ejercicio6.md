# Ejercicio 6
##Instalar juju.

Primero añadiremos el repositorio de juju `add-apt-repository ppa:juju/stable`. Y después instalaremos con apt-get `sudo apt-get install juju-core juju-local`.

Para finalizar lo configuraremos con ejecutando:

```
juju init
juju switch local
juju bootstrap
```

##Usándolo, instalar MySQL en un táper.

Entraremos al archivo de juju y modificaremos `default:amazon` por `default:local`.

Despues ejecutamos `juju deploy mysql` y `juju expose mysql`.