33-Almacenamiento-con-Longhorn-en-K0S Parte 4

En el siguiente video explico como configurar el Backup en Longhor. También hablo sobre los Snapshots

Revisaros el Video en Youtube , además os dejo el código usado: https://youtu.be/_cfzy87eGjY

Para configurar el destino de backup. Tenemos que crear un secreto con el AccessKey y SecretKey del Bucket y el EndPoint del S3 que uséis. En mi caso uso Minio.

Os dejo un ejemplo para crear un secreto usando Minio.

```
kubectl create secret generic secret-s3 -n longhorn-system --from-literal AWS_ACCESS_KEY_ID=1123456789 --from-literal AWS_ENDPOINTS=http://url.ticveintitres.com:9000 --from-literal AWS_SECRET_ACCESS_KEY=qwertyuiopasdfghjk
```

Navegar via Web a la GUI de LongHorn y en la pestaña de Setting/General , añadir el Target y el nombre del secret.

Ejemplo:

Backup Target: s3://bucket@minio/
Backup Target Credential Secret: secret-s3

Por último darle a "SAVE"

Para comprobar si esta funcionando , via GUI cambiar a la pestaña "Backup" , si no os aparecen errores todo esta correcto.

También podéis ir a un terminal y ejecutar este comando:

```
watch kubectl get backuptargets.longhorn.io -n longhorn-system
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
