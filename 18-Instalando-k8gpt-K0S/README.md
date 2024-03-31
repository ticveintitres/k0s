18-Instalando-k8sgpt-K0S

En el siguiente video explico como instalar y operar lo más basico de k8sgpt en K0S: 

Para instalarlo en Debian utilizad este comando

```
curl -LO https://github.com/k8sgpt-ai/k8sgpt/releases/download/v0.3.24/k8sgpt_amd64.deb
dpkg -i k8sgpt_amd64.deb
```

Para este ejemplo se utilizara una cuenta de OpenAI de ChatGPT. Para ello crear una Key para luego hacer login a través de k8sgpt.

![2024-03-31 16_08_53-API keys - OpenAI API — Mozilla Firefox](https://github.com/ticveintitres/k0s/assets/153328087/f0b9c58b-5bd3-41ba-91ea-f844bdf13704)

Antes de comenzar, se configura el bash completion

```
echo 'source <(k8sgpt completion bash)' >>~/.bashrc
```

Para hacer login con el token creado utilizando este comando. Pedirá el token creado, insertarlo.

```
k8sgpt auth add -b openai
```

Una vez registrado, se puede hacer un análisis para comprobar si hay problemas en el cluster usando este comando

```
k8sgpt analyze
```

Se pueden pasar varias opciones al comando, como estás:

-a : mandar datos anónimos.
-n : namespace a analizar.
-o : salida en json o text.
-e : explicar el problema.
-l : elegir el idioma , por ejemplo Spanish

Si utilizáis el plan gratuito de OpenAI como yo, al pedir que te haga una explicación te sale un mensaje diciendo que no puedes, que pagues una subscripción.

https://www.youtube.com/@ticveintitres

Creado con ❤️ por Alejandro Martínez Capilla
