# Ejercicio 4
##Instalar linux en dicho disco

Para instalar el SO en el disco solo tenemos que arrancar el disco QEMU pasandole como parametros la ISO de linux, el solo simulara la "BIOS" y se encargará de hacer que la instalación sea identica a la de una instalación en un ordenador normal

`qemu-system-x86_64 -hda nombre_disco.img -boot d -cdrom ./nombre_iso.iso -m 640` ese comando ejecuta QEMU con los indicado anteriormente, y reservar un trozo de memoria ram de 640 MB para la maquina virtual