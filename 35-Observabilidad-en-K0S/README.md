35-Observabilidad en K0S

En el siguiente video explico como configurar un stack entero de observabilidad: 

Revisaros el Video en Youtube , además os dejo el código usado:

Ejecutar en el Cluster Maestro:

Primero de todo configuraremos la parte de MetalLB, yo os dejo el siguiente código de ejemplo:

```
kubectl apply -f master-metallb.yaml
```

Lo siguiente instalaremos Grafana, os he dejado preparado un archivo que utiliza el método expuesto en la web de Grafana.

Luego tenéis que aplicar el YAML de instalación igual que si lo instalaseis de 0

```
kubectl apply -f master-grafana.yaml
```

Antes de seguir con Grafana, instalaremos Prometheus, también os he dejado el código:

```
kubectl apply -f master-prometheus.yaml
```

Luego conectarse a la web de Grafana y añadir el conector de Prometheus , estos pasos los podéis ver en el video de Youtube.

Ejecutar en el Cluster Cliente:

En el cluster cliente , hay que instalar el agente de Prometheus para que mande contenido al servidor maestro:

```
kubectl apply -f cliente-prometheus.yaml
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla