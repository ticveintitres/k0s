14-Nginx-Ingress-Controller&MetalLB-K0S
En el siguiente video explico como desplegar NGINX Ingress Controller junto con MetalLB en un cluster de K0S: https://youtu.be/-ispqFUu2Yg

Se configura un IPAddresses de MetalLB especifico para NGINX, modificar a conveniencia y ejecutad el archivo ipaddresses.yaml

```
kubectl apply -f ipaddresses.yaml
```

Como se ha añadido una nueva IPAddress a MetalLB, hay que añadir esta al L2Advertisement que se creo en el video anterior.
Se puede editar el objeto ejecutando este comando

```
kubectl edit l2advertisements.metallb.io -n metallb-system production
```

O bien ejecutando el fichero que os dejo, llamado l2advertisement.yaml, que incluye el IPAdresses nuevo. Ojo, que yo cambie de cluster y ahora mi interfaz es la "ens192", aseguraros bien de cuál es la vuestra.

```
kubectl apply -f l2advertisement.yaml
```

Para instalar NGINX Ingress Controller lo haremos con este comando sacado de su web oficial

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.10.0/deploy/static/provider/cloud/deploy.yaml
```

Una vez instalados los componentes de NGINX INGRESS CONTROLLER, podemos comprobar su funcionamiento con el fichero que os dejo llamado pod-service-ingress.yaml.
En este fichero se configura un apache con un servicio de ClusterIP y un ingress. En el fichero yo he configurado que atienda a una resolución de nombre, cambiarlo a gusto.

```
kubectl apply -f pod-service-ingress.yaml
```

Nginx Ingress Controller desplegado y configurado usando MetalLB de manera simple

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla