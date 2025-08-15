# 📚 Guía de Estudio – Sistemas Operativos 3

Resumen de comandos y prácticas para el **parcial de Sistemas Operativos 3**.  
Organizado por temas para repaso rápido y efectivo.

---

## 📑 Índice

1. [🖥 Administración básica del sistema](#-administración-básica-del-sistema)  
2. [🌐 Configuración de red con nmcli](#-configuración-de-red-con-nmcli)  
3. [👤 Gestión de usuarios y grupos](#-gestión-de-usuarios-y-grupos)  
4. [📂 Permisos de archivos](#-permisos-de-archivos)  
5. [⏰ Tareas programadas](#-tareas-programadas)  
6. [💽 Gestión de discos](#-gestión-de-discos)  
7. [🔑 Resetear contraseña root (GRUB)](#-resetear-contraseña-root-grub)  
8. [📜 Scripts útiles](#-scripts-útiles)  
9. [🌍 Servicios web y correo](#-servicios-web-y-correo)  
10. [📡 Compartir recursos](#-compartir-recursos)  
11. [🔒 Seguridad](#-seguridad)  
12. [🐳 Docker](#-docker)  

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

... (resto del contenido igual que antes) ...
