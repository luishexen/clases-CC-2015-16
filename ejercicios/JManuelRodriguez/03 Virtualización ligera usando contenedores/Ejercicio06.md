[José M. Rodríguez](https://github.com/Jmrodriguez90)

Virtualización ligera, usando contenedores: Ejercicio 6
======================================================================

1. Instalar juju.
2. Usándolo, instalar MySQL en un táper.

--

Para realizar la instalación de Juju usaremos las siguientes líneas de comando:

```
sudo add-apt-repository ppa:juju/stable
sudo apt-get update && sudo apt-get install juju-core juju-local
```

Luego nos pasamos a local con la siguiente instrucción:
`juju switch local`

y Ahora pasamos a instalar MySQL:
`sudo apt-get install mysql-server mysql-client`




