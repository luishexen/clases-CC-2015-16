#Gestión de configuraciones: Ansible

##Instala Ansible en tu sistema

Usando el gestor de paquetes para python, instalo una serie de dependencia previas con el siguiente comando

`sudo pip install paramiko PyYAML Jinja2 httplib2 six ansible`

##Configura el fichero de inventarios de las IPs de dos máquinas

Mediante `ifconfig` podemos obtener las IP's de ambas máquinas. Procedemos a añadirlo al fichero de hosts y asignárlo a la variable de entorno de ANSIBLE_HOSTS.

`echo "<IP's>" >> ./ansible_hosts export ANSIBLE_HOSTS = ./ansible_hosts`

##Usa Ansible para hacer ping a ambas máquinas

Dado que solo tenemos esas dos máquinas en el fichero de hosts disponibles:

`ansible all -m ping`

##Usa Ansible para instalar Apache en ambas máquinas

Creamos el playbook `apache.yml` :

```
---
- hosts: all
  sudo: yes
  tasks:
    - name: install apache2
      apt: name=apache2 update_cache=yes state=latest
```
Y lo ejecutamos :

`ansible-playbook apache.yml --ask-sudo-pass`

Es necesario activar la bandera de sudo dado que la instalación requiere de privilegios de root.

#Crea un "playbook" para Ansible con el que instalar PHP. Aplícalo en ambas máquinas.

Creamos el playbook `php.yml` :

```
---
- hosts:all
  sudo: yes
  tasks:
    - name: instalar PHP
      apt:pkg={{ item }} state=installed update_cache=true
      with_items:
        - php5-cli
        - php5-curl
        - php5-fpm
        - php5-intl
        - php5-json
        - php5-mcrypt
        - php5-sqlite
```
Y lo ejecutamos :

`ansible-playbook php.yml --ask-sudo-pass`

#Gestión de configuraciones: Vagrant

##Instala Vagrant en tu sistema

Dado que vagrant por defecto usa virtualbox para administrar la virtualización, nos los descargamos.

`sudo apt-get install virtualbox`

A continuación descargamos vagrant usando `apt-get` dado que no se distribuye ya como una gema.

`sudo apt-get install vagrant`

Instalar ahora el paquete dkms para asegurarnos de que los módulos del kernel de Virtualbox están correctamente actualizados.

`sudo apt-get install virtualbox-dkms`

##Baja el "box" del ejemplo (precise64.box)

En la página web de vagrantbox encontramos todas las máquinas. Al usar virtualbox buscamos la box de precise64 con dicho proveedor.

Descargamos y despleguamos la máquina :

`vagrant box add ubuntu_precise http://files.vagrantup.com/precise64.box`

##Lanza la máquina virtual y comprueba que puedes acceder a ella por ssh.

Anzes de lanzar la máquina tenemos que iniciar la configuración del proyecto. Para ello tenemos que crear un directorio raíz de nuestro proyecto y dentro generar el fichero de configuración llamando a vagrant init.

`mkdir vagrant_project`
`cd vagrant_project`
`vagrant init `
Editamos el fichero de configuración de Vagrant sustituyendo la siguiente línea.

`config.vm.box = "ubuntu_precise"`

Ya podemos iniciar el entorno mediante.

`vagrant up`

Para conectarnos a la máquina usamos.

`vagrant ssh`

Crea un Vagrantfile para instalar el nginx al arrancar la máquina

Debajo de la línea, anteriormente modificada del Vagrantfile, añadimos :

`config.vm.provision "shell", inline: "sudo apt-get update && sudo apt-get install -y nginx"`

para provisionar la máquina con nginx ( es necesario añadir el parámetro -y para que no se realizen preguntas de 'Aceptar' y se instale directamente ).

Lanzamos a continuación el comando `vagrant provision` para iniciar el proceso.

##Comprueba que nginx queda instalado y funcionando

Comprobamos en localhost el funcionamiento de la página por defecto ( o la IP que le hayamos asignado en el archivo de configuración ) de nginx o nos conectamos por ssh y comprobamos el estado del servicio.
