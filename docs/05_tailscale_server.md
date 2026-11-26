# 05 - Red Privada Virtual (Tailscale)

Para permitir el acceso remoto desde fuera de la red local (WAN) sin tener que abrir puertos en el router (lo cual es un riesgo de seguridad y a menudo falla por el CGNAT de las operadoras), se implementó **Tailscale**. 

Esta herramienta, basada en el protocolo **WireGuard**, crea una red privada virtual (VPN) cifrada de extremo a extremo, haciendo que dos ordenadores en diferentes ciudades se comporten como si estuvieran conectados por un cable al mismo router.

## 1. 🌐 Instalación en el Servidor (Fedora)

Ejecutamos el script oficial de instalación y levantamos el servicio:

```bash
# Descargar e instalar Tailscale
curl -fsSL https://tailscale.com/install.sh | sh

# Iniciar el servicio y autenticar la máquina
sudo tailscale up