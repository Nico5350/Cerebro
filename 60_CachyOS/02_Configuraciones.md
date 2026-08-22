# ⚙️ Configuraciones del Sistema

#mint #config

> Ajustes importantes del sistema Linux Mint / Cinnamon.  
> Antes de modificar archivos del sistema, hacé una copia de seguridad.

---

## 🖥️ Configuración general del escritorio (Cinnamon)

### Acceder al Panel de Control

- Menú → Preferencias → **Configuración del Sistema**
- O desde terminal: `cinnamon-settings`

### Ajustes rápidos desde terminal

```bash
cinnamon-settings display        # pantallas y resolución
cinnamon-settings keyboard       # teclado e idioma
cinnamon-settings mouse          # ratón y touchpad
cinnamon-settings power          # energía y suspensión
cinnamon-settings sound          # audio
cinnamon-settings backgrounds    # fondo de pantalla
```

---

## 🌐 Red

### Ver conexiones activas

```bash
nmcli device status
nmcli connection show
```

### Conectar / desconectar WiFi por terminal

```bash
nmcli radio wifi on                          # activar WiFi
nmcli radio wifi off                         # desactivar WiFi
nmcli dev wifi list                          # listar redes disponibles
nmcli dev wifi connect "NombreRed" password "contraseña"   # conectar
```

### DNS rápido

```bash
sudo nano /etc/resolv.conf
# Agregar:
nameserver 8.8.8.8
nameserver 1.1.1.1
```

---

## 🔋 Energía y rendimiento

### Ajustar comportamiento al cerrar tapa (laptop)

```bash
sudo nano /etc/systemd/logind.conf
```

Opciones para `HandleLidSwitch`:

- `suspend` → suspender
- `hibernate` → hibernar
- `poweroff` → apagar
- `ignore` → no hacer nada

Aplicar cambios:

```bash
sudo systemctl restart systemd-logind
```

### Gobernador de CPU

```bash
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor   # ver actual
sudo cpupower frequency-set -g performance    # máximo rendimiento
sudo cpupower frequency-set -g powersave      # ahorro de energía
```

---

## 👤 Usuarios y grupos

```bash
sudo adduser nombre               # crear usuario nuevo
sudo deluser nombre               # eliminar usuario
sudo usermod -aG sudo nombre      # dar permisos de administrador
groups nombre                     # ver grupos del usuario
```

### Cambiar nombre del equipo (hostname)

```bash
hostnamectl set-hostname nuevo-nombre
sudo nano /etc/hosts              # reemplazar el nombre viejo por el nuevo
```

---

## 🚀 Arranque del sistema (GRUB)

```bash
sudo nano /etc/default/grub
```

Opciones útiles:

```bash
GRUB_TIMEOUT=5              # segundos que espera en el menú
GRUB_DEFAULT=0              # entrada por defecto (0 = primera)
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Aplicar cambios:

```bash
sudo update-grub
```

---

## 🗂️ Repositorios y fuentes de software

```bash
sudo add-apt-repository ppa:nombre/repo    # agregar PPA
sudo add-apt-repository --remove ppa:nombre/repo   # eliminar
sudo apt update                            # refrescar lista
cat /etc/apt/sources.list                  # ver repositorios activos
```

---

## 🔒 Firewall (UFW)

```bash
sudo ufw status                    # ver estado
sudo ufw enable                    # activar
sudo ufw allow 22                  # permitir puerto SSH
sudo ufw deny 22                   # bloquear puerto
sudo ufw delete allow 22           # eliminar regla
```

---

## 🔧 Archivos de configuración importantes

|Archivo|Para qué sirve|
|---|---|
|`/etc/fstab`|Montaje automático de discos|
|`/etc/hosts`|Resolución local de nombres|
|`/etc/environment`|Variables de entorno globales|
|`/etc/crontab`|Tareas programadas del sistema|
|`~/.bashrc`|Configuración de la terminal del usuario|
|`~/.profile`|Variables y comandos al iniciar sesión|

### Aliases útiles en ~/.bashrc

```bash
nano ~/.bashrc

# Agregar al final:
alias actualizar='sudo apt update && sudo apt upgrade'
alias limpiar='sudo apt autoremove && sudo apt autoclean'
alias ll='ls -la'
alias ..='cd ..'

# Aplicar sin reiniciar:
source ~/.bashrc
```

---

_Ver también: [[01_Terminal]] | [[04_Troubleshooting]]_