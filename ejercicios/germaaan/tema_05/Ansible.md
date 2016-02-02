## Instala Ansible en tu sistema.

Si vamos a utilizar Ubuntu, depende de la versión que tengamos instalada es posible que **Ansible** se encuentre o no en los repositorios por defecto, así que nos aseguramos instalando el repositorio PPA propio de Ansible.

```
sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible -y
sudo apt-get update
sudo apt-get install ansible
```

![eje01_img01](https://dl.dropboxusercontent.com/s/mxilnqxukxvbzzi/eje01_img01.png)

![eje01_img02](https://dl.dropboxusercontent.com/s/tic1puuzgl94s0w/eje01_img02.png)


## Configura el fichero de inventario incluyendo las IPs de dos máquinas.

Para estas pruebas crearemos dos máquinas virtuales con Ubuntu Server instalado. Las direcciones IP de esas máquinas virtuales son **192.168.1.54** y **192.168.1.52**.

![eje02_img01](https://dl.dropboxusercontent.com/s/9yer8s0oycmyu5f/eje02_img01.png)

Sabiendo las direcciones IP de las máquinas, solo tenemos que crear un archivo de inventario con ambas direcciones y después exportar su ruta de acceso como variable de entorno para que Ansible sepa como acceder a él.

```
cat ~/ansible_hosts
export ANSIBLE_HOSTS=~/ansible_hosts
echo $ANSIBLE_HOSTS
```

![eje02_img02](https://dl.dropboxusercontent.com/s/bz63w3u6uuc3adi/eje02_img02.png)

## Usa Ansible para hacer ping a ambas máquinas.

Ahora que tenemos el inventario, vamos a comprobar que hay conectividad con todas las máquinas que se encuentran en él mediante _ping_. Como siempre, para conectar a un servidor la opción más cómoda es copiando primero nuestra clave SSH pública en dicho servidor, servidores en este caso.

```
ssh-copy-id -i ~/.ssh/id_rsa.pub germaaan@192.168.1.54
ssh-copy-id -i ~/.ssh/id_rsa.pub germaaan@192.168.1.52
```

![eje03_img01](https://dl.dropboxusercontent.com/s/3lpalllpx3bib7s/eje03_img01.png)

Una vez hecho esto, procedemos a ejecutar _ping_ sobre todas las máquinas en el archivo de inventario.

```
ansible all -m ping -u germaaan
```

![eje03_img02](https://dl.dropboxusercontent.com/s/vz0hr93u2uugb5q/eje03_img02.png)

## Usa Ansible para instalar Apache en ambas máquinas.

Ninguna de las máquinas tiene el servidor _Apache_ instalado.

![eje04_img01](https://dl.dropboxusercontent.com/s/b0aq3t3im1gtpke/eje04_img01.png)

Al igual que hemos hecho _ping_ a todas las máquinas del inventario a la vez, también podemos instalar un paquete en todas las máquinas a la vez. En este caso usamos el comando _command_ usando como parámetro _apt-get install -y apache_, la opción _-b_ indica que se ejecute el comando como superusuario, para lo que a su vez necesitaremos la opción _--ask-sudo-pass_.

```
ansible all -m command -a "apt-get install -y apache2" -u germaaan -b --ask-sudo-pass
```

![eje04_img02](https://dl.dropboxusercontent.com/s/l0a3rc04horzhp7/eje04_img02.png)

Si volvemos a comprobar en las máquinas virtuales, veremos que ahora _Apache_ sí se encuentra instalado y funcionando.

![eje04_img03](https://dl.dropboxusercontent.com/s/zml1jocbrljfrxr/eje04_img03.png)

Y ya que sabemos que está funcionando, vamos a comprobar que funciona correctamente.

![eje04_img04](https://dl.dropboxusercontent.com/s/tx5uzfbvvb3j49z/eje04_img04.png)

## Crea un “playbook” para Ansible con el que instalar PHP. Aplícalo en ambas máquinas.

Para automatizar una serie de tareas sin tener que ejecutarlas de una en una (que es lo realmente interesante que nos permite Ansible), vamos a crear un _playbook_ para instalar PHP en todas las máquinas. Lo primero es crear el propio _playbook_, este playbook va a ser muy simple, solo vamos a indicar que se instale en todas las máquinas (`- hosts: all`), que el usuario con el que realizar estas acciones es **germaaan** (`remote_user: germaaan`) y que la tarea a ejecutar es instalar PHP (`apt: name=php5 state=present`).

```
---
- hosts: all
  remote_user: germaaan
  tasks:
    - name: Instalar PHP
      apt: name=php5 state=present
```

Con el playbook ya listo, solo nos queda ejecutarlo para que se ejecute la configuración en todas las máquinas.

```
ansible-playbook -b php.yml --ask-sudo-pass
```

![eje05_img01](https://dl.dropboxusercontent.com/s/ykfll4brrj74ivw/eje05_img01.png)
