28-Almacenamiento-local-en-K0S

En el siguiente video explico como configurar almacenamiento local en K0S: https://youtu.be/VicqQ-H6fq8?si=p7J1RwOAHB4vkbxE

En K0S ocurre como en cualquier cluster que permita acceso a los nodos, se utiliza la plantilla de Kubernetes oficial para crear un Persistent Volume que apuntará a un directorio de uno o varios nodos.

Este directorio tiene que estar creado en todos los nodos donde se vaya a utilizar.

A diferencia de otros Drivers de Almacenamiento, aquí no se guarda objeto de PV, sino los ficheros en sí, por lo que cualquiera con acceso al nodo  o un pod con acceso al mismo contenido podria leerlo.

Os he dejado la plantilla volume-local.yaml que podéis aplicar para crear un Volumen Persistente Local. Recordar cambiar los parámetros que menciono.

```
kubectl apply -f volume-local.yaml
```

Con esta plantilla se despliega un simple Nginx con un PV y PVC para que persistan sus datos.
Si quereis comprobar que se puede acceder y crear algún fichero tan sencillo como entrar en el pod y crear un fichero y luego comprobar que existe en la ruta del nodo.

Recordad, que los comandos están pensados para ejecutarlos en mi entorno, cambiar lo que necesitéis, no copiar y pegar , a no ser que lo tengáis igual.

```
kubectl exec -it web -- bash
cd /opt/volumes
touch fichero1.txt
exit
ls /opt/volumes-k8s
```

Fácil y sencillo

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
