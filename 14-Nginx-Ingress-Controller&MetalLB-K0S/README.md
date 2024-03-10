14-Nginx-Ingress-Controller&MetalLB-K0S
En el siguiente video explico como desplegar NGINX Ingress Controller junto con MetalLB en un cluster de K0S: https://youtu.be/-ispqFUu2Yg

Se configura un IPAddresses de MetalLB especifico para NGINX, modificar a conveniencia y ejecutad el archivo ipaddresses.yaml

```

```

Para instalar NGINX Ingress Controller lo haremos con este comando sacado de su web oficial

```
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.14.3/config/manifests/metallb-native.yaml
```

Una vez instalados los componentes de MetalLB, para configurar una lista de direcciones IP ejecutar el fichero ipaddresses.yaml

```
kubectl apply -f ipaddresses.yaml
```

Ahora toca configurar la capa 2, ejecuta el fichero l2advertisement.yaml

```
kubectl apply -f l2advertisement.yaml
```

Para probar que funciona , desplegar este microservicio de prueba

```
kubectl apply -f pod-service.yaml
```

MetalLB desplegado y configurado de manera simple

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
