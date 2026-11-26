# 🖥️ Proyecto: Servidor de IA Local y Acceso Remoto Seguro (EVO-X3)

## Descripción General
Este repositorio documenta la arquitectura, instalación y configuración de un laboratorio de Inteligencia Artificial local de alto rendimiento. El sistema está diseñado para ejecutar Modelos de Lenguaje Grandes (LLMs) de forma privada, procesar documentos (RAG) y permitir el acceso remoto seguro desde redes externas sin exponer puertos vulnerables.

## 🛠️ Stack Tecnológico
*   **Hardware:** Mini PC con APU AMD (Arquitectura Strix Halo) y Memoria Unificada (128GB).
*   **Sistema Operativo:** Fedora Workstation.
*   **Motor de IA:** Ollama.
*   **Interfaz Gráfica:** Open WebUI (vía Podman/Docker).
*   **Acceso Remoto:** GNOME Remote Desktop (con TLS) + Tailscale (VPN).
*   **Seguridad:** Firewalld, SELinux y aislamiento de red (`127.0.0.1`).

## 📑 Índice de Documentación
1. [Sistema y Hardware](01_sistema_y_hardware.md)
2. [Motor de IA (Ollama)](02_motor_ia_ollama.md)
3. [Interfaz Gráfica y RAG (Open WebUI)](03_interfaz_rag_webui.md)
4. [Escritorio Remoto Seguro (TLS)](04_escritorio_remoto_tls.md)
5. [Red Privada (Tailscale)](05_red_privada_tailscale.md)
6. [Chuleta de Comandos Rápidos](06_chuleta_comandos.md)