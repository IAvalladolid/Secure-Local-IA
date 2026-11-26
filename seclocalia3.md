# 03 - Interfaz Gráfica y RAG (Open WebUI)

Este módulo documenta la instalación de **Open WebUI**, una interfaz gráfica web que nos permite interactuar con nuestros modelos locales de forma visual y segura. Además, detalla la configuración de un sistema **RAG** (Generación Aumentada por Recuperación) para que la IA pueda leer documentos en formato PDF.

## 1. 🐳 Despliegue del Contenedor (Podman/Docker)

Se utilizó Podman (con el traductor `podman-docker` instalado en Fedora) para levantar la interfaz.

> **El reto del aislamiento de red:**
> En el módulo anterior, cerramos Ollama a `127.0.0.1` por seguridad. Como Open WebUI vive dentro de un contenedor, este no podía ver a Ollama. La solución fue hacer que el contenedor comparta la red del host.

**Comando de despliegue definitivo:**
```bash
sudo docker run -d \
  --network=host \
  -v open-webui:/app/backend/data \
  -e OLLAMA_BASE_URL=http://127.0.0.1:11434 \
  --name open-webui \
  --restart always \
  ghcr.io/open-webui/open-webui:main