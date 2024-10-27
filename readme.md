## Despliegue Open WebUI en Docker 

> Domumentación oficial Open WebUI
> https://github.com/open-webui/open-webui

Instalar Container de Open WebUI
```bash
docker run -d -p 3000:8080 -e OPENAI_API_KEY=your_secret_key -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```
La aplicación web estará disponible en: 
- http://localhost:3000

## Configuración de Open WebUI

### Configuración de Providers

**Open AI**

**Google AI Studio**

**Github Models**

**Groq**

**Hyperbolic**
Al registrarse regala 10$. Tiene disponible `Qwen2.5-72B-Instruct`.
- ``API: https://api.hyperbolic.xyz/v1``


### Listado de Endpoints API Free
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