# 📚 Guía de Estudio – Sistemas Operativos 3

Resumen de comandos y prácticas para el **parcial de Sistemas Operativos 3**.  
Organizado por temas para repaso rápido y efectivo.

---

## 📑 Índice

1. [🗺 Diagrama de temas](#-diagrama-de-temas)  
2. [🖥 Administración básica del sistema](#-administración-básica-del-sistema)  
3. [🌐 Configuración de red con nmcli](#-configuración-de-red-con-nmcli)  
4. [👤 Gestión de usuarios y grupos](#-gestión-de-usuarios-y-grupos)  
5. [📂 Permisos de archivos](#-permisos-de-archivos)  
6. [⏰ Tareas programadas](#-tareas-programadas)  
7. [💽 Gestión de discos](#-gestión-de-discos)  
8. [🔑 Resetear contraseña root (GRUB)](#-resetear-contraseña-root-grub)  
9. [📜 Scripts útiles](#-scripts-útiles)  
10. [🌍 Servicios web y correo](#-servicios-web-y-correo)  
11. [📡 Compartir recursos](#-compartir-recursos)  
12. [🔒 Seguridad](#-seguridad)  
13. [🐳 Docker](#-docker)  

---

## 🗺 Diagrama de temas

```text
Sistemas Operativos 3
│
├── Administración básica
│   ├── apt update / upgrade
│   ├── Instalar / Eliminar paquetes
│   └── wget, .deb
│
├── Configuración de red (nmcli)
│   ├── DHCP
│   ├── IP estática
│   └── DNS
│
├── Gestión de usuarios
│   ├── Crear usuario
│   ├── Grupos
│   └── Permisos sudo
│
├── Permisos de archivos
│   ├── chmod
│   ├── cp / rm
│   └── Propietario / Grupo
│
├── Tareas programadas
│   ├── crontab
│   └── at
│
├── Discos
│   ├── fdisk -l
│   ├── mkfs
│   └── mount / umount
│
├── Recuperación root
│   ├── Editar GRUB
│   ├── init=/bin/bash
│   └── passwd root
│
├── Scripts
│   ├── Backup
│   └── ifconfig a archivo
│
├── Servicios
│   ├── Apache
│   ├── Postfix
│   └── Puertos 80 / 8080
│
├── Compartir recursos
│   ├── NFS
│   ├── CUPS
│   └── Rsync
│
├── Seguridad
│   ├── UFW
│   ├── IPTables
│   ├── Snort
│   └── Google Authenticator
│
└── Docker
    ├── Nginx
    ├── Portainer
    └── WordPress
```

---

## 🖥 Administración básica del sistema

| Acción | Comando |
|--------|---------|
| Actualizar sistema | `sudo apt update && sudo apt upgrade -y` |
| Buscar paquete | `apt search nombre_paquete` |
| Instalar paquete | `sudo apt install paquete` |
| Eliminar paquete | `sudo apt purge paquete` |
| Limpiar dependencias | `sudo apt autoremove` |
| Instalar .deb | `sudo apt install ./archivo.deb` |
| Descargar archivo | `wget URL` |

---

## 🌐 Configuración de red con nmcli

```bash
# Ver conexiones
nmcli con show

# DHCP
sudo nmcli con modify "Wired connection 1" ipv4.method auto
sudo nmcli con up "Wired connection 1"

# IP estática + DNS
sudo nmcli con modify "Wired connection 1" ipv4.addresses 192.168.1.100/24
sudo nmcli con modify "Wired connection 1" ipv4.gateway 192.168.1.1
sudo nmcli con modify "Wired connection 1" ipv4.dns "8.8.8.8 8.8.4.4"
sudo nmcli con modify "Wired connection 1" ipv4.method manual
sudo nmcli con up "Wired connection 1"
```

---

## 👤 Gestión de usuarios y grupos

| Acción | Comando |
|--------|---------|
| Crear usuario | `sudo adduser usuario` |
| Añadir a sudo | `sudo usermod -aG sudo usuario` |
| Crear grupo | `sudo addgroup grupo` |
| Añadir usuario a grupo | `sudo usermod -aG grupo usuario` |
| Eliminar usuario | `sudo deluser usuario --remove-home` |
| Eliminar grupo | `sudo delgroup grupo` |

---

## 📂 Permisos de archivos

```bash
chmod 700 archivo   # Solo propietario
chmod 070 archivo   # Solo grupo
cp origen destino   # Copiar
rm -r carpeta       # Eliminar
```

---

## ⏰ Tareas programadas

```bash
# Editar crontab
sudo crontab -e

# at (ejecutar en hora específica)
echo "comando" | at 10:00
atq   # Ver tareas pendientes
```

---

## 💽 Gestión de discos

```bash
sudo fdisk -l          # Listar discos
sudo mkfs.ext4 /dev/sdb  # Formatear
sudo mount /dev/sdb /ruta  # Montar
sudo umount /ruta        # Desmontar
```

---

## 🔑 Resetear contraseña root (GRUB)

1. Editar `/etc/default/grub` y cambiar:
```bash
GRUB_TIMEOUT=20
sudo update-grub
```
2. En arranque, presionar `e` y añadir:
```
init=/bin/bash
```
3. Montar en modo escritura y cambiar contraseña:
```bash
mount -o remount,rw /
passwd root
exec /sbin/init
```

---

## 📜 Scripts útiles

**Backup de /home**
```bash
tar -czvf backup-fecha.tar.gz /home/usuario
```

**Guardar ifconfig en Escritorio**
```bash
ifconfig > ~/Desktop/nombre.txt
```

---

## 🌍 Servicios web y correo

- **Apache**: configurar sitios virtuales (puertos 80 y 8080)  
- **Postfix**: enviar correo
```bash
echo "mensaje" | mail -s "Asunto" correo@dominio.com
```

---

## 📡 Compartir recursos

| Herramienta | Uso |
|-------------|-----|
| **NFS** | Compartir archivos Linux ↔ Linux |
| **CUPS** | Compartir impresoras |
| **Rsync** | Sincronizar carpetas |

Ejemplo **Rsync**:
```bash
rsync -avz origen/ usuario@IP:destino/
```

---

## 🔒 Seguridad

**UFW**
```bash
sudo ufw allow 80/tcp
sudo ufw deny 80/tcp
```

**IPTables**
```bash
sudo iptables -A INPUT -p tcp --dport 80 -j DROP
```

Herramientas extra:  
- **Snort** → IDS  
- **Google Authenticator** → 2FA SSH  

---

## 🐳 Docker

```bash
# Instalar
sudo apt install docker.io -y

# Nginx
docker run -d --name nginx -p 8888:80 -v /home/website:/usr/share/nginx/html nginx

# Portainer
docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock portainer/portainer-ce

# WordPress con Docker Compose
sudo docker-compose up -d
```

---

📌 **Tip**: Practica todos los comandos en una VM antes del examen.
