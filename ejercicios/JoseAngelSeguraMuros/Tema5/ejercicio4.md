# Ejercicio 4
##Crea una Vagrantfile para instalar nginx al arrancar la maquina.

La Vagrantfile se crea sola por defecto al bajar el box pero tendremos que incluirle un par de lineas para que se instale nginx 

```
config.vm.provision "shell", inline: <<-SHELL
     sudo apt-get update
     sudo apt-get install -y nginx
     sudo service nginx start
SHELL
```

Eso bastará para que instale nginx, ahora solo quedara redireccionar el puerto para poder acceder desde el host con esta orden en el Vagrantfile `config.vm.network "forwarded_port", guest: 80, host: 8080`

