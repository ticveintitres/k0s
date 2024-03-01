# 13-Instalar-Configurar-MetalLB-K0S
En el siguiente video explico como instalar y configurar MetalLB en un cluster de K0S: 

Esta descripción esta sacada de su página oficial:

MetalLB se conecta a su clúster de Kubernetes y proporciona una implementación de equilibrador de carga de red. En resumen, le permite crear servicios de Kubernetes de tipo LoadBalancer en clústeres que no se ejecutan en un proveedor de nube y, por lo tanto, no pueden simplemente conectarse a productos pagos para proporcionar balanceadores de carga.

He preparado estos YAML que permiten configurar MetalLB. 

Para instalar MetalLB

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
