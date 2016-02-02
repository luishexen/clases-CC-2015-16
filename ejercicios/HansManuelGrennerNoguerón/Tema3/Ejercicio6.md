**Instalar juju.**

Añadimos a los repositorios la última versión de juju, actualizamos y finalmente instalamos el programa.

```
sudo add-apt-repository ppa:juju/stable
sudo apt-get update && sudo apt-get install juju-core
```

Para inicializar el entorno del que precisa juju ejecutamos :

```juju init```

Seguimos los pasos dados para poder trabajar en local, ya que por defecto el fichero de configuración usará Amazon EC2. Abrimos el fichero de configuración por tanto:

```sudo nano /home/jmgn/.juju/environments.yaml```

Y modificamos el proveedor por defecto a local.

```default: local```


**Usándolo, instalar MySQL en un táper.**

Dado que juju requiere de sus propios contenedores con su configuración dada, pasamos a crear un llamado 'taper'. Hacemos uso del siguiente comando :

```juju bootstrap```

Ahora podemos instalar mysql :

```juju deploy mysql```
