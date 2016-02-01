[José M. Rodríguez](https://github.com/Jmrodriguez90)

Virtualización ligera, usando contenedores: Ejercicio 11
======================================================================

1. Crear a partir del contenedor anterior una imagen persistente con commit.

--

* Definir el identificador del contenedor Docker: `docker images --no-trunc`

* Guardar el estado actual del contenedor, creando una imagen persistente (commit)
```
docker commit <id_completo_contenedor> <nombre_nueva_imagen>
```

*Donde `<id_completo_contenedor>` es el identificador obtenido al ejecutar el comando del paso anterior*
