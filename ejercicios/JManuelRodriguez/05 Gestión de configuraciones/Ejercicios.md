[José M. Rodríguez](https://github.com/Jmrodriguez90)

Gestión de configuraciones: Ansible. Ejercicios
======================================================================

**Instala Ansible en tu sistema**

--

*Para instalar Ansible, hacen falta permisos de súper usuario por lo que utilizaremos sudo en la instrucción:*

`sudo apt-get install ansible`

*De no hacerlo con sudo, lanza un error.*

```
jmrodriguez90@ManuelLinux:~$ apt-get install ansible
E: No se pudo abrir el fichero de bloqueo «/var/lib/dpkg/lock» - open (13: Permiso denegado)
E: No se encontró un archivo de réplica «/var/lib/dpkg/»
jmrodriguez90@ManuelLinux:~$ sudo apt-get install ansible
[sudo] password for jmrodriguez90: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
El paquete indicado a continuación se instaló de forma automática y ya no es necesarios.
  linux-image-2.6.32-openvz-042stab112.15-amd64
Use 'apt-get autoremove' to remove it.
Paquetes sugeridos:
  ansible-doc sshpass
Se instalarán los siguientes paquetes NUEVOS:
  ansible
0 actualizados, 1 se instalarán, 0 para eliminar y 33 no actualizados.
Necesito descargar 418 kB de archivos.
Se utilizarán 2.758 kB de espacio de disco adicional después de esta operación.
Des:1 http://es.archive.ubuntu.com/ubuntu/ trusty/universe ansible all 1.5.4+dfsg-1 [418 kB]
Descargados 418 kB en 1seg. (407 kB/s)
Seleccionando el paquete ansible previamente no seleccionado.
(Leyendo la base de datos ... 454128 ficheros o directorios instalados actualmente.)
Preparing to unpack .../ansible_1.5.4+dfsg-1_all.deb ...
Unpacking ansible (1.5.4+dfsg-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Configurando ansible (1.5.4+dfsg-1) ...
jmrodriguez90@ManuelLinux:~$ 
```



====


**Configura e fichero de inventario incluyendo las IPs de dos máquinas**

--

*El fichero de inventario se configura desde la terminal de la siguiente manera*

```
jmrodriguez90@ManuelLinux:~/Escritorio/virtualizacion$ echo "192.168.0.44"> ./ansible:host
jmrodriguez90@ManuelLinux:~/Escritorio/virtualizacion$ echo "192.168.0.48">> ./ansible:host
jmrodriguez90@ManuelLinux:~/Escritorio/virtualizacion$ export ANSIBLE_HOSTS=./ansible\:host 
jmrodriguez90@ManuelLinux:~/Escritorio/virtualizacion$ cat ansible\:host 192.168.0.44
192.168.0.48
```



===


**Usa Ansible para hacer ping a ambas máquinas**

--

*AL hacer ping sobre el archivo de inventario, cada una de las ip registradas en él, responden al ping si están accesibles*

```
jmrodriguez90@ManuelLinux:~/Escritorio/virtualizacion$ ansible all -m ping -u manuel --ask-Linux123
192.168.0.44 | success >> {
	"changed": false,
	"ping": "pong"
}

192.168.0.48 | success >> {
	"changed": false,
	"ping": "pong"
}
```


===


**Usa Ansible para instalar Apache en ambas máquinas**

--

*Instalamos Apache en ambas máquinas con el siguiente comando*

`ansible all -m command -a 'apt-get install apache2' -u manuel --ask-Linux123`


===


**Crea un "PlayBook" para Ansible con el que instalar PHP. Aplícalo en ambas máquinas**

--

*Podemos crear el archivo playbook con gedit y quedaría de la siguiente manera*

```
-hosts: all
sudo: yes
-name: instalacion de php
apt: pkg=php state=installed update_cache=true
```

*Para ejecutar el archivo playbook, usamos la siguiente línea de comandos*

`ansible-playbook ./playbook.yml -u manuel --ask-Linux123 --ask-sudo-Linux123`

*De esta manera queda instalado el PHP en todas las máquinas*


===



