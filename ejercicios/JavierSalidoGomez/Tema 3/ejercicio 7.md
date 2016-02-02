## Ejercicio 7: Destruir toda la configuración creada anteriormente. Volver a crear la máquina anterior y añadirle mediawiki y una relación entre ellos. Crear un script en shell para reproducir la configuración usada en las máquinas que hagan falta.

Para evitar desmontar servicios y máquinas manualmente, se usa el comando: 

    juju destroy-environment local 
    
para destruir el entorno local con todo lo que lo conforma.

Volvemos a crear la máquina anterior al igual que se hizo para el ejercicio 6:



    juju bootstrap
    juju deploy mysql

Salvo que ahora añadimos tambien mediawiki y lo relacionamos con mysql:

    juju deploy mediawiki
    juju add-relation mediawiki mysql
    
    

El script contendría:
    
    juju init
    sed -i 's/default: amazon/default: local/g' ~/.juju/environments.yaml
    juju switch local
    juju bootstrap
    juju deploy mysql
    juju deploy mediawiki
    juju add-relation mediawiki mysql
    juju expose mediawiki
    





