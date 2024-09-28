36-Servidor de Minecraft JAVA en Kubernetes

En el siguiente video explico como desplegar un servidor de Minecraft JAVA utilizando la imagen de LGSM: https://youtu.be/GoSOqfJbTXA

Revisaros el Video en Youtube , además os dejo el código usado: 

DESPLIEGUE SENCILLO

Se trata de desplegar un pod y exponer el puerto de Minecraft.

```
kubectl run minecraft --image=gameservermanagers/gameserver:mc
kubectl expose pod minecraft --type=LoadBalancer --port=25565
```

Este método es sencillo pero no es lo mas adecuado para gestionar luego la infraestructura.

DESPLIEGUE AVANZADO

Para este método, os dejo el fichero YAML con los objetos a desplegar. Para ello se desplegará un NAMESPACE, un PVC que solicite a LONGHORN un PV , un DEPLOYMENT donde se configura la imagen y por último un SERVICE para exponer

```
kubectl apply -f minecraft-java.yaml
```
Con esto tenemos mas control sobre que datos vamos a guardar y tenemos la posibilidad de luego realizar copias de seguridad del PV, además de la persistencia.

CONFIGURANDO EL SERVIDOR

Una vez desplegado el servidor podemos configurar todos los archivos que hay dentro de /data , ya que persistirán los datos. Para escribir datos en el fichero server.properties de Minecraft puedes conectarte al pod o simplemente editarlo con este comando.

```
kubectl exec -it -n minecraft nombrepod -- nano serverfiles/server.properties
kubectl delete pods -n minecraft nombrepod
```

Una vez guardados los datos, hay que renovar el pod, y con eso tendriamos los nuevos datos aplicados. Recordad que en un servidor normal, tendriamos que reiniciar los servicios, por lo que la perdida de servicio también se aplica, de igual modo que si eliminamos el pod o hacemos un rollout del deployment.

CONFIGURACION RCON

Si eres de los que se conectan al Servidor de Minecraft con RCON para administrarlo. Lo primero que hay que hacer es configurar la Variable en el fichero de server.properties. Seguid los pasos anteriores de editar el fichero server.properties, y cambiad el "false" por el "true" ene la Variable "enable.rcon". Aplicad los cambios eliminando el pod y ya estaría listo para conectarse.

Si eres como yo, que no tienes el Binario para poder conectarte por RCON, en Debian seguid los siguientes pasos:

1- Descargar el GIT de RCON

```
git clone https://github.com/Tiiffi/mcrcon.git
```

2- Compilarlo con MAKE, si no lo tenéis , se instala
```
apt install -y make build-essential libssl-dev
cd mcrcon
make
mv mcrcon /usr/local/bin
```
3- Por último hacer una conexión a vuestro servidor usando los credenciales que aparecen en la Variable "rcon.password" en el fichero "server.properties"

```
mcrcon -H 10.23.23.202 -p password
```

El resto de la explicación podéis verla en el video.

Fácil y sencillo, más en mi canal 👍

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla