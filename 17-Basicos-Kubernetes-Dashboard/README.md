17-Básicos-Kubernetes-Dashboard-K0S

En el siguiente video explico como operar de forma básica el Dashboard de Kubernetes oficial: https://youtu.be/15vrTZ6mzJU

En este repositorio de código he dejado un fichero de ejemplo que podéis usar para probar Kubernetes Dashboard.

Recordad, que para hacer login con el token hay que sacar el token, este comando a modo de ejemplo:

```
kubectl create token -n kubernetes-dashboard nombreserviceaccount
```

Para aplicar cualquier fichero utilizad en siguiente comando:

```
kubectl apply -f fichero.yaml
```

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
