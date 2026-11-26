<img width="1920" height="1048" alt="Screenshot From 2026-11-26 19-46-10" src="https://github.com/user-attachments/assets/733cfac4-3eff-4538-a254-ebd74d238bab" />
<img width="1920" height="1048" alt="Screenshot From 2026-11-26 19-44-36" src="https://github.com/user-attachments/assets/f5a7a211-9656-48c8-a90e-1570baadb5bd" />
<img width="1920" height="1048" alt="Screenshot From 2026-11-26 19-31-51" src="https://github.com/user-attachments/assets/2048fb5e-d7f0-4d60-a687-82689fed7123" />
# 🧠 Secure Local AI Lab (Strix Halo Edition)

![Status](https://img.shields.io/badge/Status-Active-success)
![OS](https://img.shields.io/badge/OS-Fedora_Workstation-blue)
![Engine](https://img.shields.io/badge/Engine-Ollama-orange)
![UI](https://img.shields.io/badge/UI-Open_WebUI-blueviolet)
![VPN](https://img.shields.io/badge/VPN-Tailscale-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

## 📖 Descripción General
Este repositorio contiene la arquitectura, configuración y documentación técnica de un **Laboratorio de Inteligencia Artificial Local de alto rendimiento**. 

El proyecto está diseñado para ejecutar Modelos de Lenguaje Grandes (LLMs) de forma 100% privada, procesar documentos locales (RAG) y permitir un acceso remoto seguro desde redes externas, sin depender de servicios en la nube y evitando exponer puertos vulnerables en el router.

### 💻 Hardware Base
El laboratorio está montado sobre un Mini PC con arquitectura **AMD Strix Halo** (Ryzen AI Max+), aprovechando su **Memoria Unificada (128 GB)** para asignar grandes cantidades de VRAM a la GPU integrada, permitiendo ejecutar modelos de hasta 70B/120B parámetros de forma local.

---

## ✨ Características Principales
*   🔒 **Privacidad Total:** Ningún dato, prompt o documento sale de la red local.
*   🚀 **Inferencia Local:** Uso de Ollama para servir modelos como Qwen 2.5 (14B y 32B).
*   📚 **Sistema RAG Integrado:** Capacidad de subir documentos PDF y chatear con ellos usando Open WebUI y `nomic-embed-text`.
*   🛡️ **Acceso Remoto Seguro (Zero Trust):** Conexión cifrada de extremo a extremo mediante VPN (Tailscale) y escritorio remoto RDP con certificados TLS autofirmados.
*   🐳 **Entorno Contenerizado:** Despliegue aislado de la interfaz gráfica mediante Podman/Docker.

---

## 📂 Estructura del Repositorio

La documentación técnica está modularizada para facilitar su lectura y mantenimiento. Puedes encontrar los detalles de cada módulo en la carpeta `docs/`:

| Módulo | Descripción |
| :--- | :--- |
| [01 - Sistema y Hardware](docs/01_sistema_y_hardware.md) | Verificación del sistema y gestión de Memoria Unificada (UMA). |
| [02 - Motor de IA (Ollama)](docs/02_motor_ia_ollama.md) | Instalación de Ollama y blindaje de seguridad (Localhost). |
| [03 - Interfaz y RAG](docs/03_interfaz_rag_webui.md) | Despliegue de Open WebUI y configuración de Embeddings. |
| [04 - Escritorio Remoto (TLS)](docs/04_escritorio_remoto_tls.md) | Configuración de RDP seguro con certificados TLS y SELinux. |
| [05 - Red Privada (Tailscale)](docs/05_red_privada_tailscale.md) | Implementación de VPN para acceso remoto sin abrir puertos. |
| [06 - Chuleta de Comandos](docs/06_chuleta_comandos.md) | Referencia rápida de comandos de administración. |

---

## 🛠️ Stack Tecnológico
*   **Sistema Operativo:** Fedora Workstation (Kernel 6.18+)
*   **Motor de Inferencia:** [Ollama](https://ollama.com/)
*   **Interfaz Gráfica:** [Open WebUI](https://github.com/open-webui/open-webui)
*   **Virtualización:** Podman / Docker
*   **Redes:** Tailscale (WireGuard), Firewalld, GNOME Remote Desktop (RDP).

---

## 🚀 Despliegue Rápido (Quick Start)

Si deseas replicar este entorno, sigue el orden de los documentos en la carpeta `docs/`. El flujo recomendado es:

1.  Preparar el sistema operativo y verificar la GPU.
2.  Instalar Ollama y descargar los modelos base (`qwen2.5:14b`, `nomic-embed-text`).
3.  Desplegar Open WebUI con red de host para conectar con Ollama.
4.  Configurar los certificados TLS para el escritorio remoto.
5.  Instalar Tailscale para habilitar el acceso WAN.

> ⚠️ **Nota de Seguridad:** Por defecto, Ollama está configurado para escuchar únicamente en `127.0.0.1`. Si modificas esta configuración, asegúrate de contar con reglas de cortafuegos estrictas.

---

## 📄 Licencia
Este proyecto está bajo la Licencia MIT. Consulta el archivo [LICENSE](LICENSE) para más detalles.

---
*Documentación creada y mantenida con pasión por la ingeniería y la privacidad de datos.*
