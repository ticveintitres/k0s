41 - NextCloud en Kubernetes

En el siguiente video explico como configurar una instancia de NextCloud en Kubernetes usando K0S: 
Revisaros el Video en Youtube , además os dejo el código usado: 

Os dejo el código para desplegarlo en el fichero nextcloud.yaml

```
kubectl apply -f nextcloud.yaml
```

Para este caso de uso, lo he instalado sin certificado SSL. Si queréis que tenga certificado , tenéis que configurarle un Ingress, con un certificado TLS de forma manual o usando por ejemplo Lets Encrypt. Tenéis la explicación sobre como usar Lets Encrypt en el video: https://youtu.be/L-MQ-cU6MEc

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla