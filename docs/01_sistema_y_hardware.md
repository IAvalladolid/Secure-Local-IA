# 01 - Sistema Base y Hardware

## 1. Hardware y Memoria Unificada (UMA)
El equipo cuenta con una arquitectura de memoria unificada, donde la RAM y la VRAM comparten el mismo espacio físico. Por defecto, la BIOS reserva 64 GB como *Frame Buffer* para la GPU. Por lo tanto, el sistema operativo reportará ~62 GB de RAM disponibles.

### Verificación del Sistema
Para comprobar que el kernel (versión 7.2+) detecta correctamente el hardware:
```bash
uname -r                  # Verificar versión del kernel
free -h                   # Ver memoria RAM disponible en el SO
lspci | grep -i amd       # Comprobar detección de la GPU (Radeon 8060S)
fastfetch                 # Resumen visual del sistema