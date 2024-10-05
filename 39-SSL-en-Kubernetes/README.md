39-SSL-en-Kubernetes de forma sencilla

En el siguiente video explico como configurar certificados SSL en Kubernetes de forma sencilla: https://youtu.be/L-MQ-cU6MEc

Revisaros el Video en Youtube , además os dejo el código usado: 

MODO MANUAL

Os dejo el codigo en el archivo ejemplo-manual.yaml

```
kubectl apply -f ejemplo-manual.yaml
```

USANDO CERTMANAGER

Para este metodo instalamos Certmanager

```
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.16.0/cert-manager.yaml
```

Luego creamos un ClusterIssuer o Issuer, en mi caso un Issuer, y se configura para usar Let's Encrypt

```
kubectl apply -f issuer.yaml
```

Por último desplegar la aplicación de prueba

```
kubectl apply -f ejemplo-certmanager.yaml
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla