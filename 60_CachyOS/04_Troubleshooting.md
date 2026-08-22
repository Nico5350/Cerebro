# 🔧 Troubleshooting — Solución de Problemas

#mint #fix #troubleshooting

> Problemas comunes en Linux Mint y cómo resolverlos.  
> Si el problema persiste, revisar logs con `journalctl -xe`

---

## 📦 Problemas con paquetes y actualizaciones

### Error: "dpkg was interrupted"

```bash
sudo dpkg --configure -a
sudo apt install -f
```

### Paquetes rotos o dependencias faltantes

```bash
sudo apt install -f                  # reparar dependencias
sudo dpkg --configure -a             # configurar paquetes pendientes
sudo apt clean                       # limpiar caché
sudo apt update && sudo apt upgrade
```

### "E: Unable to lock the administration directory"

```bash
sudo rm /var/lib/dpkg/lock-frontend
sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
sudo dpkg --configure -a
```

### Repositorio con error de clave GPG

```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CLAVE_AQUI
# O usando la nueva forma:
sudo gpg --keyserver keyserver.ubuntu.com --recv-keys CLAVE
sudo gpg --export CLAVE | sudo tee /etc/apt/trusted.gpg.d/nombre.gpg
```

---

## 🖥️ Problemas gráficos y pantalla

### Pantalla negra al iniciar

1. En GRUB, presionar `e` sobre la entrada de Linux Mint
2. Buscar la línea con `quiet splash`
3. Reemplazar por `nomodeset`
4. Presionar `Ctrl + X` para arrancar
5. Una vez dentro, instalar drivers correctos

### Cinnamon crashea / pantalla congelada

```bash
# Reiniciar Cinnamon sin cerrar sesión (Alt+F2 → escribir):
r

# O desde terminal:
cinnamon --replace &
```

### Resolución incorrecta / monitor no detectado

```bash
xrandr                             # ver pantallas y resoluciones
xrandr --output HDMI-1 --auto     # autodetectar monitor externo
cinnamon-settings display          # abrir configuración de pantallas
```

### Drivers de video NVIDIA

```bash
sudo apt install nvidia-driver-535    # instalar driver (verificar versión)
# O usar el Gestor de Controladores:
# Menú → Administración → Gestor de controladores
```

---

## 🔊 Problemas de audio

### Sin sonido

```bash
pulseaudio --kill && pulseaudio --start    # reiniciar PulseAudio
alsamixer                                  # verificar que no esté muteado
pavucontrol                               # control de volumen avanzado
```

### Audio distorsionado o con lag

```bash
sudo nano /etc/pulse/default.pa
# Agregar al final:
load-module module-udev-detect tsched=0
# Reiniciar:
pulseaudio --kill && pulseaudio --start
```

---

## 🌐 Problemas de red

### WiFi no conecta o se desconecta

```bash
sudo systemctl restart NetworkManager
nmcli networking off && nmcli networking on
```

### Olvidé la contraseña del WiFi guardado

```bash
sudo cat /etc/NetworkManager/system-connections/"Nombre Red.nmconnection"
# Buscar la línea: psk=contraseña
```

### Sin internet pero hay conexión

```bash
ping 8.8.8.8             # probar conectividad
ping google.com          # probar DNS
# Si el primero funciona pero el segundo no → problema de DNS
sudo nano /etc/resolv.conf
# Agregar: nameserver 8.8.8.8
```

---

## 💾 Problemas de disco y archivos

### Ver errores en el sistema de archivos

```bash
sudo dmesg | grep -i error
sudo fsck /dev/sdX        # revisar disco (con el sistema desmontado)
```

### Disco lleno de repente

```bash
df -h                                  # ver uso general
du -sh /*                              # ver qué carpeta ocupa más
sudo apt clean                         # limpiar caché de paquetes
sudo journalctl --vacuum-size=100M     # reducir logs del sistema
```

### No puedo montar un disco/USB

```bash
lsblk                                  # listar dispositivos
sudo mount /dev/sdX1 /mnt              # montar manualmente
sudo fdisk -l                          # ver particiones
```

---

## 🔑 Problemas de permisos

### "Permission denied" en un archivo

```bash
ls -la archivo                         # ver permisos actuales
chmod 755 archivo                      # dar permisos de ejecución
sudo chown $USER:$USER archivo         # tomar posesión del archivo
```

### No puedo ejecutar un script

```bash
chmod +x script.sh
./script.sh
```

---

## 🚀 Problemas al iniciar el sistema

### El sistema tarda mucho en arrancar

```bash
systemd-analyze                        # tiempo total de arranque
systemd-analyze blame                  # qué servicio tarda más
systemd-analyze critical-chain         # cadena crítica de servicios
sudo systemctl disable servicio        # desactivar servicios lentos innecesarios
```

### GRUB no aparece al iniciar

```bash
# Arrancar desde live USB y luego:
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
sudo update-grub
```

---

## 📋 Logs útiles para diagnosticar

```bash
journalctl -xe                          # logs recientes del sistema
journalctl -u nombre-servicio           # logs de un servicio específico
journalctl --since "1 hour ago"         # logs de la última hora
dmesg | tail -50                        # mensajes del kernel
cat /var/log/syslog | tail -100         # log general del sistema
cat /var/log/Xorg.0.log | grep EE      # errores del servidor gráfico
```

---

_Ver también: [[01_Terminal]] | [[02_Configuraciones]]_