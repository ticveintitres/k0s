20-Instalando Lens de Mirantis como IDE para K0S

En el siguiente video explico como instalar Lens de Mirantis para usarlo para gestionar clusters, como en K0S: 

Para instalarlo , lo mejor es ir a su página de descarga y descargarse la versión para vuestro sistema operativo: https://k8slens.dev/download

--imagen descarga lens--

Una vez instalado en nuestro sistema operativo, al ejecutarlo nos pedirá un registro. Nos registramos para poder acceder:

--imagen registro lens--

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
