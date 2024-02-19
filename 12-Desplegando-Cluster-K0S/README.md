# 12-Desplegando Cluster K0S
En el siguiente video explico como desplegar un Cluster de Kubernetes utilizando la solución de K0S: 

Utilizo 2 máquinas Debian Linux, una de las máquinas se utilizará como ControlPlane y la otra máquinas como Worker.

Instalar los binarios de K0S

```
wget https://github.com/k0sproject/k0sctl/releases/download/v0.17.4/k0sctl-linux-x64
chmod +x k0sctl
mv k0sctl /usr/local/bin
curl -sSLf https://get.k0s.sh | bash
echo 'source <(k0s completion bash)' >>~/.bashrc
```

Configurar el autocompletado del comando k0sctl 

```
echo 'source <(k0sctl completion bash)' >>~/.bashrc
echo 'source <(k0s completion bash)' >>~/.bashrc
```

Desplegar cluster utilizando el fichero que hay en el repositorio

```
k0sctl apply --config desplegar-cluster.yaml
```

Acceder via web, configurar Wordpress y escribir una entrada a modo de prueba.

Realizar el backup de Wordpress con Velero. Para ello la forma más básica es lanzando un backup a demanda

```
velero create backup prueba-wordpress --include-namespaces wordpress --default-volumes-to-restic=true
```

Revisar el estado del backup , y comprobar que este completado y sin errores
```
velero get backup
```

Ahora para comprobar que el backup se ha realizado correctamente y se han guardado los datos nuevos, borrar la aplicación de Wordpress de prueba.

```
kubectl delete -f prueba.yaml
```

Una vez borrada del todo ( comprobar que no exista el Namespace y los Persistent Volumes), se hace un Restore desde Velero
```
velero restore create prueba-restore --from-backup prueba-wordpress
```

Se comprueba que el trabajo de Restore de Velero ha finalizado.
```
velero get restore
```

Se comprueba que se han desplegado todos los objetos de Wordpress
```
kubectl get all -n wordpress
kubectl get pv
```

Por último ingresar via web al Wordpress y comprobar que todo se ha recuperado.

Si todo salio correctamente, se ha recuperado la aplicación de Wordpress desde una copia de seguridad con Velero

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
