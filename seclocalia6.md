# 06 - Chuleta de Comandos Rápidos (Cheat Sheet)

Guía de referencia rápida con los comandos esenciales utilizados en la administración de este laboratorio. Ideal para consultar de un vistazo.

## 🤖 Gestión de Ollama (IA Local)
| Comando | Descripción |
| :--- | :--- |
| `ollama run [modelo]` | Descarga (si falta) y ejecuta el modelo en la terminal. |
| `ollama pull [modelo]` | Solo descarga el modelo a disco (útil para prepararlo antes). |
| `ollama list` | Lista todos los modelos descargados en el sistema. |
| `ollama ps` | Muestra qué modelos están cargados en RAM/VRAM ahora mismo. |
| `ollama rm [modelo]` | Elimina un modelo del disco para liberar espacio. |
| `/set verbose` | *(Dentro del chat)* Activa las métricas de tokens/s. |
| `/bye` | *(Dentro del chat)* Sale del modelo y vuelve a la terminal. |

## 🐳 Gestión de Contenedores (Open WebUI)
| Comando | Descripción |
| :--- | :--- |
| `sudo docker ps` | Ver contenedores activos en este momento. |
| `sudo docker ps -a` | Ver todos los contenedores (incluidos los detenidos). |
| `sudo docker logs [nombre]` | Ver los registros (logs) de un contenedor. Vital para ver errores. |
| `sudo docker restart [nombre]` | Reiniciar un contenedor específico. |
| `sudo docker rm -f [nombre]` | Eliminar un contenedor a la fuerza (los datos en volúmenes se conservan). |

## ⚙️ Gestión de Servicios (Systemd)
| Comando | Descripción |
| :--- | :--- |
| `sudo systemctl status [servicio]` | Ver el estado de un servicio (ej. `ollama`). Pulsar `q` para salir. |
| `sudo systemctl restart [servicio]` | Reiniciar un servicio para aplicar cambios. |
| `sudo systemctl edit [servicio]` | Abrir el editor para modificar la configuración de un servicio. |
| `sudo systemctl daemon-reload` | Recargar systemd si hemos modificado archivos de configuración. |

## 🌐 Red y Diagnóstico
| Comando | Descripción |
| :--- | :--- |
| `sudo ss -tlnp \| grep [puerto]` | Ver qué programa escucha en un puerto y si es local (`127.0.0.1`) o público (`*`). |
| `ip a` | Ver las direcciones IP de las interfaces de red. |
| `ping [IP]` | Comprobar si hay conectividad con otro equipo. |
| `tailscale ip -4` | Ver la IP privada asignada por la VPN. |
| `tailscale status` | Ver el estado de la red virtual y los equipos conectados. |

## 🛡️ Cortafuegos (Firewalld)
| Comando | Descripción |
| :--- | :--- |
| `sudo firewall-cmd --list-all` | Ver todas las reglas y puertos abiertos actualmente. |
| `sudo firewall-cmd --permanent --add-port=[puerto]/tcp` | Abrir un puerto específico de forma permanente. |
| `sudo firewall-cmd --permanent --remove-port=[puerto]/tcp` | Cerrar un puerto específico. |
| `sudo firewall-cmd --reload` | Aplicar los cambios permanentes (obligatorio tras añadir/quitar). |

## 🦅 Seguridad (SELinux)
| Comando | Descripción |
| :--- | :--- |
| `sudo restorecon -Rv [ruta]` | Corregir los contextos de seguridad tras mover archivos. |
| `sudo ausearch -m avc -ts recent` | Buscar bloqueos recientes de SELinux (útil si algo falla sin motivo). |
| `sudo setenforce 0` | Poner SELinux en modo permisivo temporal (se revierte al reiniciar). |

---
> 💡 **Consejo Pro:** Puedes crear "alias" en tu archivo `~/.bashrc` para los comandos más largos. Por ejemplo: `alias ollama-ps='ollama ps'`.