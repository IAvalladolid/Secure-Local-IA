# 02 - Motor de IA Local (Ollama)

## 1. Instalación
Se instaló Ollama mediante su script oficial. Los modelos descargados inicialmente para pruebas de rendimiento y contexto son:
*   `qwen2.5:14b` (Equilibrio rendimiento/velocidad).
*   `qwen2.5:32b` (Mayor razonamiento, requiere más VRAM).
*   `nomic-embed-text` (Modelo especializado en generar *embeddings* para RAG).

## 2. Blindaje de Seguridad
Por defecto, Ollama escucha en `0.0.0.0` (todas las interfaces de red). Para evitar accesos no autorizados desde la red local, se modificó su servicio para que escuche únicamente en `127.0.0.1` (localhost).

**Configuración aplicada:**
```bash
sudo systemctl edit ollama.service