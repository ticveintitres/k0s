51 - Instalando Minio Productivo

En el siguiente video explico como instalar MinIO para un entorno productivo con certificados TLS, usando un cluster de K0S: https://youtu.be/Tb6tMuJvHYc

Revisaros el Video en Youtube , además os dejo el código usado: 

Os dejo el siguiente código:

Como instalar el Operador

```
kubectl apply -k "github.com/minio/operator?ref=v6.0.4"
```

Como instalar minIO usando el operador con certificados de Lets Encrypt

```
kubectl apply -f con-operador-lets-encrypt.yaml
```

Como instalar minIO sin usar el operador con certificados autofirmados

```
kubectl apply -f sin-operador-tls-propio.yaml
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo ( para vosotros, yo me tiré 3 semanas de mi vida, gracias gente de minIO, muy majos eh), más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla