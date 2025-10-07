90 - Instalación de K0S en modo Airgapped por TicVeintitres

En el siguiente video explico como instalar un pequeño cluster de K0S en modo Airgap o Offline, para entornos sin acceso a Internet: https://youtu.be/2DaOqY3hR0s

Revisaros el Video en Youtube , además os dejo el código usado: 

Os dejo las instrucciones:

MAQUINA CON INTERNET

Estos dos comandos descargarán la paquetería para K0S

```
k0s airgap list-images --all > airgap-images.txt
k0s airgap bundle-artifacts -v -o image-bundle.tar < airgap-images.txt
```

Mover los ficheros a cada uno de los nodos de Kubernetes, podeis usar como ejemplo este comando, solamente cambiar la IP por las vuestras.

```
scp image-bundle.tar root@192.168.0.38:/root/image-bundle.tar
scp image-bundle.tar root@192.168.0.39:/root/image-bundle.tar
```

CONTROLPLANE 1

En el nodo Controlplane ejecutar lo siguiente para arrancar el Cluster:

Crear el directorio donde van la paquetería y copiar los datos a ella

```
mkdir -p /var/lib/k0s/images
cp image-bundle.tar /var/lib/k0s/images/
```

Instalar K0S en el primer Controlplane:

```
k0s install controller --enable-worker
```

Arrancar K0S

```
k0s start
```

Crear el Token para el Nodo Worker
```
k0s token create --role=worker --expiry=24h  > token-file
```

Mover el Token al Nodo Worker

```
scp token-file root@192.168.0.39:/root/token-file
```


WORKER 1

En el nodo Worker ejecutar lo siguiente para arrancar el Cluster:

Crear el directorio donde van la paquetería y copiar los datos a ella

```
mkdir -p /var/lib/k0s/images
cp image-bundle.tar /var/lib/k0s/images/
```

Instalar K0S en el primer Worker usando el Token para unirlo al Cluster

```
k0s install worker --token-file token-file
```

Arrancar K0S

```
k0s start
```

DESDE EL CONTROLPLANE1

Para ver si el cluster esta levantado usar el los siguientes comandos para ver los nodos Ready y los Pods Running

```
k0s kubectl get nodes
k0s kubectl get pods -A
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla