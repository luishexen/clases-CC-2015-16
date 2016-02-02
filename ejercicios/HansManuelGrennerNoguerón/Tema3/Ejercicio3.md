**Crear y ejecutar un contenedor basado en Debian.**

De la misma forma que se menciona en el ejercicio anterior el proceso de instalación para usar una distribución diferente consiste en modificar el parámetro **-t** de la función **lxc-create**. Al tratarse de una distribución basada en Debian ( igual que ubuntu ) en este caso eligiremos una versión debian original:

```
sudo lxc-create -t debian -n caja-debian
sudo lxc-start -n caja-debian
sudo lxc-console -n caja-debian
```
