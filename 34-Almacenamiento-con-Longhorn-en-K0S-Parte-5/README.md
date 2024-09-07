34-Almacenamiento-con-Longhorn-en-K0S Parte 5

En el siguiente video explico como actualizar LongHorn en K0S.

Revisaros el Video en Youtube , además os dejo el código usado: 

Para actualizar Longhorn primero de todo tenéis que leeros en la página oficial si vuestra versión es compatible con la nueva versión a la que queréis actualizar.

Luego tenéis que aplicar el YAML de instalación igual que si lo instalaseis de 0

```
kubectl apply -f https://raw.githubusercontent.com/longhorn/longhorn/v1.7.1/deploy/longhorn.yaml
```

Comenzará a desplegar los nuevos pods e irá decomisando los viejos.

Los unicos pods que permanecerán arriba serán los del tipo "engine", esto es debido a que el proceso de actualización no los borra porque estarán siendo usados por los volúmenes existentes.

Lo siguientes es ir a la GUI de Longhorn y actualizar los Volúmenes.

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla