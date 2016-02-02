## Instala Vagrant en tu sistema.

Instalamos **Vagrant** como cualquier otro paquete.

```
sudo apt-get install vagrant
```

![eje01_img01](https://dl.dropboxusercontent.com/s/ixnapprhrm23zxn/eje01_img01.png)

## Baja el “box” del ejemplo (precise64.box).

Ahora descargaremos el _box_ que vamos a crear la máquina virtual, concretamente la versión de Ubuntu 12.04 de 64 bits.

```
vagrant box add precise64 http://files.vagrantup.com/precise64.box
```

![eje01_img02](https://dl.dropboxusercontent.com/s/kolamd9tl23q1h7/eje01_img02.png)

## Lanza la máquina virtual y comprueba que puedes acceder a ella por ssh.

Para poder crear la máquina virtual, creamos primero un archivo de configuración Vagrantfile para nuestra máquina virtual (`vagrant init`), después ya podemos levantar la máquina para usarla (`vagrant up`). Cuando el proceso finalice, pobramos a acceder a ella mediante SSH (`vagrant ssh`).

```
vagrant init precise64
vagrant up
vagrant ssh
```

![eje01_img03](https://dl.dropboxusercontent.com/s/61jmlp1ffse5tbq/eje01_img03.png)

## Crea un Vagrantfile para instalar el nginx al arrancar la máquina.

Modificamos el Vagrantfile para añadirle una configuración de provisionamiento mediante comandos, concretamente que cada vez que se inicie la máquina se actualice la lista de paquetes y se intente instalar el servidor _nginx_.

```
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "precise64"
  config.vm.network :private_network, ip: "192.168.2.50"

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y nginx
  SHELL
end
```

## Comprueba que nginx queda instalado y funcionando.

Para comprobar que la configuración que hemos creado en la sección anterior funciona, probar a provisionar la máquina.

```
vagrant provision
```

![eje01_img04](https://dl.dropboxusercontent.com/s/n3qdwewc9wis4kd/eje01_img04.png)

Volvemos a la máquina y comprobamos que el servidor está instalado y funcionando.

![eje01_img05.png](https://dl.dropboxusercontent.com/s/uafl23t274s3ile/eje01_img05.png)

Desde el navegador de nuestro sistema, comprobamos que el servidor funciona correctamente y es accesible.

![eje01_img06](https://dl.dropboxusercontent.com/s/29xhdo0yp2flv4l/eje01_img06.png)
