19-K8sgpt-y-Trivy-K0S

En el siguiente video explico como instalar Trivy en k8sgpt, y como utilizarlo, en K0S: https://youtu.be/Vf6-mgU7YfI

Para activar trivy en el cluster usando k8sgpt utilizad este comando. De paso crearemos un namespace llamado k8sgpt

```
kubectl create ns k8sgpt
k8sgpt integration activate trivy -n k8sgpt
```

Instalara unos pods en el namespace "k8sgpt" que permitirán escanear el cluster o lo que necesitemos de él.

Para escanear el cluster entero ejecutar este comando

```
k8sgpt analyze
```

Nos aparecerá todos los objetos que pueden tener vulnerabilidades, y nos comenta como podemos arreglar cada vulnerabilidad. Además son validos todos los parámetros que de por sí tiene "k8sgpt anaylize" como sacarlo en formato JSON "-o json"

El formato es similar , por no decir igual al de Trivy, nos saca los resultados con una escala de gravedad tip "MEDIUM", "HIGH"

De este modo tenemos un escaner de vulnerabilidades compatible con k8sgpt, que permite utilizar la inteligencia artificial.

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
