30-Almacenamiento-con-Longhorn-en-K0S Parte 1

En el siguiente video explico como configurar almacenamiento NFS en un Cluster de Kubernetes con K0S: https://youtu.be/i6AnSa1bCyM

Revisaros el Video en Youtube , además os dejo el código usado:

He usado este código de la página oficial de LongHorn para descargar y instalar: 

```
kubectl apply -f https://raw.githubusercontent.com/longhorn/longhorn/v1.6.2/deploy/longhorn.yaml
```

Os dejo dos ficheros de despliegue de prueba con dos tipos de almacenamiento.

RWO

```
kubectl apply -f ejemplo-rwo.yaml
```

RWX

```
kubectl apply -f ejemplo-rwx.yaml
```

Fácil y sencillo , en el siguiente video mostraré la GUI de LongHorn

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
