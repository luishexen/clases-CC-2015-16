#Ansible

##Instala Ansible en tu sistema.

En primer lugar se añade el PPA:

    sudo apt-add-repository ppa:ansible/ansible
    
Se actualiza:

    sudo apt-get update
    
Y se instala:

    sudo apt-get install ansible

##Configura el fichero de inventario incluyendo las IPs de dos máquinas. 

Primero usamos ifconfig y buscamos el eth0 en ambas máquinas virtuales

Una vez las obtenemos hacemos un fichero inventario y añadimos ambas IP con:  
    
    echo IP_maquina1 >> ./ansible_host 
    echo IP_maquina2 >> ./ansible_host
       
Y lo exportamos como variable de entorno:

    export ANSIBLE_HOST=./ansible_host

##Usa Ansible para hacer ping a ambas máquinas. 

Usamos el comando:

    ansible all -m ping -u ubuntu -ask-pass

Realmente esta haciendo ping a todas las máquinas comprobando su accesibilidad.
Siendo ubuntu el nombre del usuario.

##Usa Ansible para instalar Apache en ambas máquinas. 

Usamos el comando:

    ansible all -m command -a 'sudo apt-get install apache2' -u ubuntu --ask-pass
   
Entre comillas ponemos el comando que se quiere ejecutar en las máquinas virtuales, en este caso el comando para instalar apache.

##Crea un “playbook” para Ansible con el que instalar PHP. Aplícalo en ambas máquinas. 

En primer lugar, creamos el archivo php_playbook.yml.

Para crear el playbook se usa la sintaxis yml quedando así:

    -host: all
    sudo: yes
    tasks:
       -name: Instalar PHP
       apt: pkg=php5 state=latest update_cache=true
       with_items:
          - php5-cli
          - php5-curl
          - php5-fpm
          - php5-intl
          - php5-json
          - php5-mcrypt
          - php5-sqlite
       
       
Donde en with_items se especifican herramientas extras que se requiera instalar, no necesario en esta ocasion.

Y se ejecuta con el comando:

    ansible-playbook ./php_playbook.yml -u ubuntu --ask-pass --ask-sudo-pass



