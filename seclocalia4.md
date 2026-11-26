# 04 - Escritorio Remoto Seguro (GNOME Remote Desktop)

Para permitir el acceso remoto desde otros equipos sin exponer conexiones sin cifrar, se habilitó el protocolo RDP de GNOME en el puerto `3390` y se configuró un certificado TLS autofirmado. Esta configuración es fundamental para eliminar el aviso de "Conexión no segura" (Insecure Connection) en los clientes Windows y garantizar que los datos viajen cifrados.

## 1. 🔐 Generación y Aplicación del Certificado TLS

El servicio `gnome-remote-desktop` corre a nivel de sistema (bajo el usuario `root`). Si intentamos darle un certificado que está en nuestra carpeta personal, SELinux o los permisos de Linux lo bloquearán. Por eso, lo generamos directamente en su carpeta segura.

**Paso a paso (ejecutar en la terminal del servidor):**

```bash
# 1. Generar la clave privada y el certificado (Usa la IP Local como Common Name)
# NOTA: Cuando pregunte por el "Common Name", se debe introducir la IP local (ej. 192.168.1.36)
sudo openssl req -new -x509 -newkey rsa:2048 \
  -keyout /etc/gnome-remote-desktop/tls.key \
  -out /etc/gnome-remote-desktop/tls.crt \
  -days 365 -nodes

# 2. Ceder la propiedad de los archivos al servicio
sudo chown gnome-remote-desktop:gnome-remote-desktop /etc/gnome-remote-desktop/tls.key /etc/gnome-remote-desktop/tls.crt

# 3. Establecer permisos estrictos (solo el dueño puede leer la clave privada)
sudo chmod 600 /etc/gnome-remote-desktop/tls.key
sudo chmod 644 /etc/gnome-remote-desktop/tls.crt

# 4. Dar el contexto correcto a SELinux (Vital en Fedora)
sudo restorecon -Rv /etc/gnome-remote-desktop/

# 5. Aplicar el certificado y la clave al servicio
sudo grdctl --system rdp set-tls-key /etc/gnome-remote-desktop/tls.key
sudo grdctl --system rdp set-tls-cert /etc/gnome-remote-desktop/tls.crt

# 6. Reiniciar el servicio para aplicar los cambios
sudo systemctl restart gnome-remote-desktop.service