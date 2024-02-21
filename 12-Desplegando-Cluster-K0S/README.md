# 12-Desplegando Cluster K0S
En el siguiente video explico como desplegar un Cluster de Kubernetes utilizando la solución de K0S: https://youtu.be/Nxo5j54M1-s

Utilizo 2 máquinas Debian Linux, una de las máquinas se utilizará como ControlPlane y la otra máquinas como Worker.

Instalar los binarios de K0S en el Controlplane y Worker.

```
wget https://github.com/k0sproject/k0sctl/releases/download/v0.17.4/k0sctl-linux-x64
chmod +x k0sctl
mv k0sctl /usr/local/bin
curl -sSLf https://get.k0s.sh | bash
echo 'source <(k0s completion bash)' >>~/.bashrc
```

Configurar el autocompletado del comando k0sctl  en el Controlplane y Worker

```
echo 'source <(k0sctl completion bash)' >>~/.bashrc
echo 'source <(k0s completion bash)' >>~/.bashrc
```

Desplegar cluster utilizando el fichero que hay en el repositorio

```
k0sctl apply --config desplegar-cluster.yaml
```

Conectarse al Controlplane y sacar el kubeconfig.

```
k0s kubeconfig admin > .kube/config
```

Revisar si ha instalado correctamente
```
kubectl get nodes
kubectl get pods -A
```

Listo, cluster desplegado

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
