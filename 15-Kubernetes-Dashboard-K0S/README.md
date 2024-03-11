15-Kubernetes-Dashboard-K0S
En el siguiente video explico como desplegar el Dashboard de Kubernetes oficial junto con MetalLB en un cluster de K0S: https://youtu.be/-ispqFUu2Yg

Se configura un IPAddresses de MetalLB especifico para el Dashboard de Kubernets, modificar a conveniencia y ejecutad el archivo ipaddresses.yaml

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

Para instalar el Dashboard de Kubernetes, he dejado este fichero llamado "dashboard.yaml", que incluye la modificación del Servicio para que sea de tipo LoadBalancer, y no ClusterIP como dicen en la página oficial de Kubernetes.

```
kubectl apply -f dashboard.yaml
```

Una vez instalados los componentes del dashboard de Kubernetes, acceder via web.

```

```

Kubernetes Dashboard instalado en el cluster de K0s

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla