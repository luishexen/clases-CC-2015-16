## Ejercicio 11: Crear a partir del contenedor anterior una imagen persistente con commit.


En primer lugar debemos conocer el ID del contenedor sobre el que queremos crear la imagen persistente. Para ello usamos el comando:

    sudo docker ps -a -notrunc 
    
Una vez obtenemos el identificador del contenedor, usamos el siguiente comando:

    sudo docker commit ID_CONTENEDOR NOMBRE_DE_LA_NUEVA_IMAGEN
    
   
