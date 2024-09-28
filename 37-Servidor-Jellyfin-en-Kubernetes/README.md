37-Servidor Jellyfin en Kubernetes

En el siguiente video explico como desplegar un servidor de Jellyfin en Kubernetes: 

Revisaros el Video en Youtube , además os dejo el código usado: 

DESPLIEGUE SENCILLO

Se trata de desplegar un pod y exponer el puerto de Minecraft.

```
kubectl run minecraft --image=jellyfin/jellyfin:2024092305
kubectl expose pod jellyfin --type=LoadBalancer --port=8096
```

Este método es sencillo pero no es lo mas adecuado para gestionar luego la infraestructura.

DESPLIEGUE AVANZADO

Para este método, os dejo el fichero YAML con los objetos a desplegar. Para ello se desplegará un NAMESPACE, 3 PVCs que se solicitarán al CSI NFS 3 PVs, un DEPLOYMENT donde se configura la imagen y por último un SERVICE para exponer.
Es recomendable utilizar 3 PVs como mínimo, donde uno guardará la información de la configuración del servidor, otro lo dedicaremos para la Cache, y el tercero y posteriores para guardar las fotos, videos,musica, libros...etc

```
kubectl apply -f jellyfin.yaml
```
Con esto tenemos mas control sobre que datos vamos a guardar y tenemos la posibilidad de luego realizar copias de seguridad del PV, además de la persistencia.

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla