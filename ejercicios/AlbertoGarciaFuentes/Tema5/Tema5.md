# Ejercicio 1
##Instala Vagrant en tu sistema

Instalamos **Vagrant** como cualquier otro paquete.

```
sudo apt-get install vagrant
```

# Ejercicio 2
##Baja el box del ejemplo (precise64.box)

Con el siguiente comando:

```
vagrant box add precise64 http://files.vagrantup.com/precise64.box
```

# Ejercicio 3
##Lanza la maquina virtual y comprueba que puedes acceder a ella por ssh


Para poder crear la máquina virtual creamos primero un archivo de configuración Vagrantfile para nuestra máquina virtual con `vagrant init`.

Después ya podemos levantar la máquina para usarla (`vagrant up`). 

Cuando el proceso finalice, pobramos a acceder a ella mediante SSH (`vagrant ssh`).

```
vagrant init precise64
vagrant up
vagrant ssh
```

# Ejercicio 4
##Crea una Vagrantfile para instalar nginx al arrancar la maquina.

Añadimos algunas lineas para que instale nginx: 

```
config.vm.provision "shell", inline: <<-SHELL
     sudo apt-get update
     sudo apt-get install -y nginx
     sudo service nginx start
SHELL
```

# Ejercicio 5
##Comprueba que nginx esta instalado y funcionando

Desde el navegador de nuestro sistema, comprobamos que el servidor funciona correctamente y es accesible.

