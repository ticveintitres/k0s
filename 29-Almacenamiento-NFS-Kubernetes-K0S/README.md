29-Almacenamiento-NFS-en-Kubernetes-K0S

En el siguiente video explico como configurar almacenamiento NFS en un Cluster de Kubernetes con K0S:

Para mi hay 3 formas de usar el almacenamiento NFS en Kubernetes. 

1 - Se trata de añadir la cadena de conexión directamente en el código del pod, sin necesidad de crear PVs ni PVCs. Este método es igual que si conectases una máquina virtual a un directorio NFS.

No crea PVs ni PVCs, y los datos pueden ser leídos por cualquiera que tenga acceso al directorio NFS.

Os dejo este fichero de prueba llamado "solucion-1.yaml" para que probéis.

```
kubectl apply -f solucion-1.yaml
```

2 - En este caso creamos un PV y un PVC, es en el PV donde añadimos la cadena de conexión hacia el directorio NFS, y en el POD declaramos el volúmen desde un PVC.

Por mucho que se creen los objetos en Kubernetes de PV y PVC, en el directorio NFS no se ve reflejado la creación de un objeto de PV, y es igual que en la forma 1, donde los datos pueden ser leídos por cualquiera que tenga acceso al directorio NFS.

Os dejo este fichero de prueba llamado "solucion-2.yaml" para que probéis.

```
kubectl apply -f solucion-2.yaml
```

3 - Esta opción es la más completa y adecuada, ya que instalaremos un CSI NFS. Este CSI es uno de los recomendados por la documentación oficial de Kubernetes. Creará una StorageClass que podrás usar para crear PVs y PVCs.

De esta manera en el directorio NFS si se crearán objetos de PV ,lo que facilita que el dato no este en plano y este dentro de un PV.

Os dejo este fichero de prueba llamado "solucion-3.yaml" para que probéis. Pero antes, tendréis que instalar el CSI, lo podéis hacer con HELM.

```
helm repo add nfs-subdir-external-provisioner https://kubernetes-sigs.github.io/nfs-subdir-external-provisioner/
```

```
helm install nfs-subdir-external-provisioner nfs-subdir-external-provisioner/nfs-subdir-external-provisioner 
--namespace=nfs-csi \
--create-namespace \
--set nfs.server=10.23.23.18 \
--set nfs.path=/opt/nfs/ticveintitres2 \
--set storageClass.name=nfs-csi
```

```
kubectl apply -f solucion-3.yaml
```

Fácil y sencillo

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
