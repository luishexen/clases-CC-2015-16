**Instala Ansible en tu sistema**

Ansible usa una serie de módulos de python que necesitan ser instalados previamente para su [correcto funcionamiento](http://docs.ansible.com/ansible/intro_installation.html#getting-ansible). Usando el gestor de paquetes para python :

```sudo pip install paramiko PyYAML Jinja2 httplib2 six ansible```


**Configura el fichero de inventarios de las IPs de dos máquinas**

Mediante ifconfig podemos obtener las IP's de ambas máquinas. Procedemos a añadirlo al fichero de hosts y asignárlo a la variable de entorno de ANSIBLE_HOSTS.


```echo "<IP's>" >> ./ansible_hosts
export ANSIBLE_HOSTS = ./ansible_hosts```

**Usa Ansible para hacer ping a ambas máquinas**

Dado que solo tenemos esas dos máquinas en el fichero de hosts disponibles:

```ansible all -m ping```

**Usa Ansible para instalar Apache en ambas máquinas**

Creamos el playbook **apache.yml** :

```
---
- hosts: all
  sudo: yes
  tasks:
    - name: install apache2
      apt: name=apache2 update_cache=yes state=latest
```

Y lo ejecutamos :

```ansible-playbook apache.yml --ask-sudo-pass```

Es necesario activar la bandera de sudo dado que la instalación requiere de privilegios de root.

**Crea un "playbook" para Ansible con el que instalar PHP. Aplícalo en ambas máquinas.**

Creamos el playbook **php.yml** :

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

```ansible-playbook php.yml --ask-sudo-pass```

