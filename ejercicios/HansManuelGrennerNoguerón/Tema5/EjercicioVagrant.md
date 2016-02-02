**Instala Vagrant en tu sistema**

Dado que vagrant por defecto usa virtualbox para administrar la virtualización, nos los descargamos.

```sudo apt-get install virtualbox```

A continuación descargamos vagrant usando ```apt-get`` dado que no se distribuye ya como una gema. En caso de tenerlo previamente instalado con una gema se recomiendo desintalarlo primero ```sudo gem uninstall vagrant```.

```sudo apt-get install vagrant```

Instalar ahora el paquete dkms para asegurarnos de que los módulos del kernel de Virtualbox están correctamente actualizados.

```sudo apt-get install virtualbox-dkms```


**Baja el "box" del ejemplo (precise64.box)**

En la página web de [vagrantbox](http://www.vagrantbox.es/) encontramos todas las máquinas. Al usar virtualbox buscamos la box de precise64 con dicho proveedor.

Descargamos y despleguamos la máquina : 

```vagrant box add ubuntu_precise http://files.vagrantup.com/precise64.box```


**Lanza la máquina virtual y comprueba que puedes acceder a ella por ssh.**

Anzes de lanzar la máquina tenemos que iniciar la configuración del proyecto. Para ello tenemos que crear un directorio raíz de nuestro proyecto y dentro generar el fichero de configuración llamando a ```vagrant init```.

```
mkdir vagrant_project
cd vagrant_project
vagrant init 
```

Editamos el fichero de configuración de Vagrant sustituyendo la siguiente línea.

```config.vm.box = "ubuntu_precise"```

Ya podemos iniciar el entorno mediante.

```vagrant up```

Para conectarnos a la máquina usamos.

```vagrant ssh```


**Crea un Vagrantfile para instalar el nginx al arrancar la máquina**

Debajo de la línea, anteriormente modificada del Vagrantfile, añadimos :

```config.vm.provision "shell", inline: "sudo apt-get update && sudo apt-get install -y nginx"```

para provisionar la máquina con nginx ( es necesario aádir el parámetro ```-y``` para que no se realizen preguntas de 'Aceptar' y se instale directamente ).

Lanzamos a continuación el comando ```vagrant provision``` para iniciar el proceso.


**Comprueba que nginx queda instalado y funcionando**

Comprobamos en localhost el funcionamiento de la página por defecto ( o la IP que le hayamos asignado en el archivo de configuración ) de nginx o nos conectamos por ssh y comprobamos el estado del servicio.


