48 - Horizontal Pod Autoscaler

En el siguiente video explico configurar de forma sencilla el Horizontal Pod Autoscaler usando un cluster de K0S: https://youtu.be/eR6_9viB_3s

Revisaros el Video en Youtube , además os dejo el código usado: 

Os dejo el código para desplegarlo en el fichero hpa-ejemplo.yaml

```
kubectl apply -f hpa-ejemplo.yaml
```
Para realizar el BenchMark instalar las apache2-utils

´´´
apt install -y apache2-utils
´´´

Y este el comando para realizar el BenchMark

```
ab -n 10000 -c 100 http://10.23.23.201:80/
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla