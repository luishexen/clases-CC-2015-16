##1.- Instala Vagran en tu sistema


	```sh
	 $ sudo vagrant up 
	```
	![imagenvagran1](https://dl.dropboxusercontent.com/s/iu7l9d3ztp90vkn/imagen_Vagrant_1.png?dl=0)

##2.- Baja el "box" del ejemplo (precise 64 )
	

	```sh
		$ vagrant box add precise64
	```
	![imagen_box](https://dl.dropboxusercontent.com/s/vnwtiqpoljc8vps/imagen_vagrant_2.png?dl=0)
##3.- Lanza la máquina virtual y comprueba que puedes acceder a ella por ssh
	
	```sh
		$ sudo vagran ssh
	```
	![imagen_vagean_2](https://dl.dropboxusercontent.com/s/gzz0maqhywhdt0u/imagen_vangrant_2.png?dl=0)

##4.- Crea un Vagrantfile para instalar el nginx al arrancar la máquina
	
	```sh
	      	$ sudo apt-get install gnix	
	```


##5.- Comprueba que nginx queda instalado y funciona


