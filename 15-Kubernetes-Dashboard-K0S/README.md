15-Kubernetes-Dashboard-K0S

En el siguiente video explico como desplegar el Dashboard de Kubernetes oficial junto con MetalLB en un cluster de K0S: https://youtu.be/89lsxUc7tL4

Se configura un IPAddresses de MetalLB especifico para el Dashboard de Kubernets, modificar a conveniencia y ejecutad el archivo ipaddresses.yaml

```
kubectl apply -f ipaddresses.yaml
```

Como se ha añadido una nueva IPAddress a MetalLB, hay que añadir esta al L2Advertisement que se creo en el video anterior.
Se puede editar el objeto ejecutando este comando

```
kubectl edit l2advertisements.metallb.io -n metallb-system production
```

O bien ejecutando el fichero que os dejo, llamado l2advertisement.yaml, que incluye el IPAdresses nuevo.

```
kubectl apply -f l2advertisement.yaml
```

Para instalar el Dashboard de Kubernetes, he dejado este fichero llamado "dashboard.yaml", que incluye la modificación del Servicio para que sea de tipo LoadBalancer, y no ClusterIP como dicen en la página oficial de Kubernetes.

```
kubectl apply -f dashboard.yaml
```

Una vez instalados los componentes del dashboard de Kubernetes, acceder via web.
El acceso esta configurado por Token, y por defecto no se crea ningún usuario. 
Para configurar un usuario , hay que crear una serviceaccount y asignarle el ClusterRole cluster-admin. Usar los siguientes comandos.

![imagen](https://github.com/ticveintitres/k0s/assets/153328087/92cf5f41-e9e3-435f-a187-109c7f369317)

```
kubectl create sa ticveintitres -n kubernetes-dashboard
kubectl create clusterrolebinding --clusterrole cluster-admin --serviceaccount kubernetes-dashboard:ticveintitres ticveintitres-admin
```

Para sacar el token utilizad este comando:

```
kubectl create token -n kubernetes-dashboard ticveintitres
```

Kubernetes Dashboard instalado en el cluster de K0s

![imagen](https://github.com/ticveintitres/k0s/assets/153328087/7db443a5-793a-4336-ab9b-08b404eb1b3d)

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
