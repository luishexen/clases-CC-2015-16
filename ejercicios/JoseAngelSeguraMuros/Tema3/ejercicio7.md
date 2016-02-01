# Ejercicio 7
##Destruir toda la configuración creada anteriormente


##Volver a crear la máquina anterior y añadirle mediawiki y una relación entre ellos.

Partiendo del ejercicion anterior ejecutaremos  `juju deploy mysql` y `juju deploy mediawiki` para tener los contenedores listos. Crearemos la relacion entre ellos con `juju add-relation mediawiki:db mysql`. Y por ultimo finalizaremos con  `juju expose mediawiki`

##Crear un script en shell para reproducir la configuración usada en las máquinas que hagan falta.

```
juju bootstrap
juju deploy mysql
juju deploy mediawiki
juju add-relation mediawiki:db mysql
juju expose mediawiki
```


