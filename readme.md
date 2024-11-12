## Despliegue Open WebUI en Docker 

> Domumentación oficial Open WebUI
> https://github.com/open-webui/open-webui

Se hace el pull de la imagen y se ejecuta el contenedor con el comando (bash):
```bash
docker run -d -p 3000:8080 -e OPENAI_API_KEY=your_secret_key -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```
Al ejecutar el comando se descargará la imagen (tarda un rato) y se creará un contenedor con el nombre `open-webui` que se ejecutará en segundo plano. La aplicación web estará disponible en: http://localhost:3000

Al entrar por primera vez en Open WebUI, se debe crear la Cuenta de Inicio. Esta cuenta será de Administrador.

## Configuración de Open WebUI

### Configuración de Providers

##### Open AI
Sólo hay que registrar la API Key de OpenAI y se cargarán los modelos disponibles.

#####  Google AI Studio
No hay una URL disponible para crear un conector directo. Se puede utilzar un Pipeline o una Function. 
Usar la Function: https://openwebui.com/f/justinrahb/google_genai
Se instala la Function y se configura con la API Key de Google AI Studio. 
Finalmente se activa y se cargarán los modelos disponibles de Google AI Studio.

Límites de uso de Google AI Studio: https://ai.google.dev/pricing

##### Github Models
No hay una URL disponible para crear un conector directo. Se puede utilzar un Pipeline o una Function. 
Usar la Function: https://openwebui.com/f/jscheah/github_models_manifold
Se instala la Function y se configura el PAT (Personnal Access Token) de Github. 
Finalmente se activa y se cargarán los modelos disponibles de Google AI Studio.

Modelos disponibles: https://github.com/marketplace/models
Límtes de uso de Github Models: https://docs.github.com/en/github-models/prototyping-with-ai-models#rate-limits

##### Groq
En Connections se configura la URL de la API de Groq 2 y se registra la API Key.
URL de la API: https://api.groq.com/openai/v1

URL de Groq Console: https://console.groq.com

##### Groq 2
En Connections se configura la URL de la API de Groq 2 y se registra la API Key.
URL de la API: https://api.x.ai/v1

URL de X AI Console: https://console.x.ai/

##### Listado de Endpoints API Free
En este sitio de github se puede encontrar un listado de API Endpoints Free para probar en Open WebUI
https://github.com/cheahjs/free-llm-api-resources 



### Configuración de Models accesibles para Usuarios

### Configuración de Models

### Comfiguración de Prompts

### Confuguración de Functions


## Publicación en Internet mediente ngrok

> Documentación oficial
> https://dashboard.ngrok.com/get-started/setup/windows

**Instalación y configuración de ngrok en Windows**

Para instalar ngrok en Windows, se descarga el exe de la página oficial.
Para probar si funciona, se configura el authtoken con el comando:
```bash
ngrok config add-authtoken <your_auth_token>
```
Para exponer Open WebUI en una URL estática, se ejecuta el comando:
```bash
ngrok http --url=[URL estática dada por ngrok] 3000
```

**Despliegue de ngrok como servicio de Windows**

Con `ngrok.exe` se puede crear un servicio de Windows para que se ejecute automáticamente al iniciar el sistema operativo. Para ello, se ejecuta el comando (en cmd con permisos de administrador):
```bash
ngrok service install --config [path]\ngrok.yml
```
Donde `ngrok.yml` es un archivo de configuración con el siguiente contenido:
```yaml
version: "2"
authtoken: [authtoken]
tunnels:
  basic:
    proto: http
    addr: 3000
    domain: [static_url]
```
Para desinstalar el servicio, se ejecuta el comando:
```bash
ngrok service uninstall
```



## Acceso a la API REST de Open WebUI