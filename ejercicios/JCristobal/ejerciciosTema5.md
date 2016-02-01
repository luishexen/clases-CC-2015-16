**José Cristóbal López Zafra - Ejercicios del [tema 5](https://dl.dropboxusercontent.com/u/4144051/cc_t4_t5.html)**

##**Gestión de configuraciones: [Ansible](http://es.slideshare.net/pacvslideshare/cloud-computing-gestin-de-configuraciones-ansible)**

### Instala Ansible en tu sistema

Simplemente ejecutamos `sudo apt-get install ansible`

### Configura el fichero de inventario de las IPs de dos máquinas

Sabiendo sus IPs, las añadimos al fichero con:

`echo "IP de la máquina" >> ./ansible_hosts`
 
`export ANSIBLE_HOSTS=./ansible_hosts`

### Usa Ansible para hacer ping a ambas máquinas

Hacemos ping con `ansible all  -m ping -u pedro  --ask-pass` (usuario "pedro" ya que usamos la máquina Debian que proporciona el profesor)

### Usa Ansible para instalar Apache en ambas máquinas

Lo hacemos sin "playbook", mediante el comando `ansible all -m command -a 'sudo apt-get install -y apache2' -u pedro --ask-pass --ask-sudo-pass`

### Crea un "playbook" para Ansible con el que instalar PHP. Amplicalo en ambas máquinas.

Creamos un "playbook" llamado "ansible_playbook_php.yml" para instalar varios paquetes de PHP, que contenga:

```
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

Y ejecutamos: `ansible-playbook ansible_playbook_php.yml -u pedro --ask-pass --ask-sudo-pass`


##**Gestión de configuraciones: [Vagrant](http://es.slideshare.net/pacvslideshare/cloud-computing-gestin-de-configuraciones-vagrant)**

### Instalar Vagrant en tu sistema

Accedo a https://www.vagrantup.com/downloads.html , escojo mi SO e inicio el proceso de [instalación](https://i.gyazo.com/ee5be0d41f8685e4407e9ebfeaae5539.png).

### Baja el "box" del ejemplo (precise64.box)

Accedo a la web https://www.vagrantbox.es/ y buscamos el "box":

![lista](https://i.gyazo.com/009e9052679c709839354aa7c4645e2d.png)

Y ejecuto `vagrant box add precise64  http://files.vagrantup.com/precise64.box`

[Captura del "box" bajado](https://i.gyazo.com/9b9cd1a18d7d2e6813e24937f39e4347.png)

### Lanza la máquina virtual y comprueba que puedes acceder a ella por ssh

La iniciamos con `vagrant init precise64`, se crea el "Vagrantfile", y ya podemos lanzarla: `vagrat up`

[Lanzando máquina](https://i.gyazo.com/1cfe0b6a048bf4ba2ecd4c9b2695a792.png)

Ejecutamos `vagrant ssh` y nos conectamos:

![conexión ssh](https://i.gyazo.com/40306693355960416f3f364aca4b3c11.png)


### Crea un Vagrantfile para instalar el nginx al arrancar la máquina

Modificamos el Vagranfile, añadiendo al final:

![instalar nginx](http://i.imgur.com/2U1a8hF.png)

y ejecutamos `vagrant provision`.


### Comprueba que nginx queda instalado y funcionando

Accedemos mediante ssh y vemos que está instalado:

![nginx instalado](http://i.imgur.com/eDGGiZx.png)

y funcionando:

![nginx funcionando](https://i.gyazo.com/d893541e71e936a7d3b14afdabbb9c81.png)




