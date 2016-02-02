## Ejercicio 10: Crear un usuario propio e instalar nginx en el contenedor creado de esta forma.


Para esto elegimos una de las imágenes creadas. En primer lugar, hay que conectar con la máquina elegida a través del comando:

    sudo docker run -i -t mongo /bin/bash
    
Donde "mongo" es el nombre de mi máquina elegida.

Ahora simplemente hay que usar el comando:

    sudo apt-get install nginx
    
Y:

    service nginx start

Para instalar y arrancar el servicio de nginx

Para comprobar mediante el navegador que el correcto funcionamiento de nginx habría que establecer el puerto al ejecutar el shell con la máquina de la siguiente forma:

    sudo docker run -p puerto -i -t mongo /bin/bash  


![](http://googledrive.com/host/0ByKPAGLB_FgcU1E3LVk2dWxsVzA/3-10-1.png)

    