30-Almacenamiento-con-Longhorn-en-K0S Parte 2

En el siguiente video explico como acceder a la web de Longhorn y darle un toque de seguridad:

Revisaros el Video en Youtube , además os dejo el código usado:

Os dejo el código para crear el ingress para Longhorn, para aplicarlo usad: 

```
kubectl apply -f ingress-longhorn.yaml
```

Para crear el secreto, necesitais las apache2-utils, para instalarlas:

```
apt install -y apache2-utils
```

Para crear el secreto utilizad este codigo:

```
htpasswd -c auth longhorn-user
kubectl create secret generic longhorn-basic-auth --from-file=auth -n longhorn-system
```

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
