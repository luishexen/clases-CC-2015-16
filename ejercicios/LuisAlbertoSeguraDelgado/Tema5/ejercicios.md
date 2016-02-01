# Ejercicios del Tema 5

### Ejercicios

La instalación de Vagrant en Mac OSX es muy sencilla, simplemente descargar y ejecutar el instalador desde su web: [https://www.vagrantup.com/downloads.html](https://www.vagrantup.com/downloads.html).

Una vez instalado, ya podemos descargar y utilizar la caja de precise64. Para ello, usamos los siguiente comandos:

```
vagrant box add precise64 http://files.vagrantup.com/precise64.box
```

![](http://imgur.com/HAuUFKt.png)

Ahora ya podemos iniciar nuestra máquina con `vagrant up` y acceder mediante SSH con `vagrant ssh`.

![](http://imgur.com/P7GOfpB.png)


Para instalar nginx desde el Vagrantfile tenemos que añadir las siguientes lineas al final del fichero (en el fichero que se ha generado automaticamente ya debe estar esta sección y solo hará falta descomentar e indicar que queremos instalar nginx):

```
config.vm.provision "shell", inline: <<-SHELL
     sudo apt-get update
     sudo apt-get install -y nginx
     sudo service nginx start
SHELL
```

Para poder acceder al servidor web desde el host, tambien necesitaremos incluir la siguiente linea a nuestro Vagrantfile `config.vm.network "forwarded_port", guest: 80, host: 8080`

![](http://imgur.com/s9hb3gc.png)

Una vez instalado nginx, podemos acceder al servidor para comprobar que esta instalado usando e puerto que habíamos redireccionado a nuestro host anteriormente.

![](http://i.imgur.com/2xEkCeq.png)
