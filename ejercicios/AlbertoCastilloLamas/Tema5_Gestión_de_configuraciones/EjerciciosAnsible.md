# Ejercicios
## Instalar Ansible en tu sistema

`apt-get install ansible`

![Ejercicos_1](http://googledrive.com/host/0B5Yam2FWqtZPa19NUmY1NE1uOTA/Ejercicios_1.png)

##Configura el equipo de inventario incluyendo las IPs de dos máquinas

Ponemos en ejecución dos máquinas y obtenemos la dirección IP de cada una

`ifconfig`

**172.17.42.117**  IP_1
**172.17.42.118**  IP_2

Creamos el inventario para poner ambas máquinas bajo el control de Ansible, para mi caso

```
echo <IP_1> >> ./ansible_host
echo <IP_2> >> ./ansible_host
```

E insertamos inventario para Ansible

`export ANSIBLE_HOST=./ansible_host`


##Usa ansible para hacer ping a ambas máquinas

`ansible all -m ping -u alcasla --ask-pass


##Usa ansible para instalar apache en ambas máquinas

`ansible all -m command -a 'sudo apt-get install apache2' -u alcasla --ask-pass


##Crea un "playbook" para Ansible con el que instalar PHP. Aplícalo a ambas máquinas.

![Ejercicos_2](http://googledrive.com/host/0B5Yam2FWqtZPa19NUmY1NE1uOTA/Ejercicios_2.png)

Lo ejecutamos para que se instale en todas las máquinas

`ansible-playbook ./playbook.yml -u alcasla --ask-passs --ask-sudo-pass`