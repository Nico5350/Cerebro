# 🖥️ Terminal — Comandos útiles

#mint #terminal

> Referencia rápida de comandos para Linux Mint.  
> Los comandos con `sudo` requieren contraseña de administrador.

---

## 📦 Sistema y paquetes

### Actualizar el sistema

```bash
sudo apt update                        # actualizar lista de paquetes
sudo apt upgrade                       # instalar actualizaciones
sudo apt update && sudo apt upgrade    # ambos de una vez
sudo apt full-upgrade                  # actualización completa (puede remover paquetes)
```

### Instalar / desinstalar apps

```bash
sudo apt install nombre-app            # instalar
sudo apt remove nombre-app             # desinstalar (conserva config)
sudo apt purge nombre-app              # desinstalar + borrar config
sudo apt autoremove                    # limpiar paquetes huérfanos
```

### Buscar paquetes

```bash
apt search nombre                      # buscar en repositorios
apt show nombre-app                    # ver info de un paquete
dpkg -l | grep nombre                  # ver si está instalado
```

---

## 💾 Archivos y directorios

### Navegación

```bash
pwd                   # mostrar directorio actual
ls                    # listar archivos
ls -la                # listar con detalles y ocultos
cd carpeta            # entrar a carpeta
cd ..                 # subir un nivel
cd ~                  # ir al home
cd -                  # volver al directorio anterior
```

### Crear / copiar / mover / borrar

```bash
mkdir carpeta                  # crear carpeta
mkdir -p ruta/subcarpeta       # crear carpeta con subdirectorios
touch archivo.txt              # crear archivo vacío
cp origen destino              # copiar archivo
cp -r carpeta destino          # copiar carpeta completa
mv origen destino              # mover o renombrar
rm archivo                     # borrar archivo
rm -rf carpeta                 # borrar carpeta completa (¡cuidado!)
```

### Buscar

```bash
find / -name "archivo.txt"         # buscar por nombre
find ~ -name "*.pdf"               # buscar PDFs en home
grep -r "texto" /ruta              # buscar texto dentro de archivos
locate nombre                      # búsqueda rápida (usa índice)
```

---

## 🔍 Sistema y procesos

### Información del sistema

```bash
uname -a                  # info del kernel
lsb_release -a            # versión de Linux Mint
hostname                  # nombre del equipo
whoami                    # usuario actual
uptime                    # tiempo encendido
```

### Uso de recursos

```bash
htop                      # monitor interactivo (más visual)
top                       # monitor básico
df -h                     # espacio en disco (legible)
du -sh carpeta            # tamaño de una carpeta
free -h                   # uso de RAM
```

### Procesos

```bash
ps aux                        # listar todos los procesos
ps aux | grep nombre          # buscar proceso por nombre
kill PID                      # terminar proceso por ID
killall nombre-proceso        # terminar por nombre
```

---

## 🌐 Red

```bash
ip a                          # ver IPs y adaptadores
ping google.com               # probar conexión
curl ifconfig.me              # ver IP pública
nmcli device status           # estado de conexiones de red
ss -tuln                      # ver puertos abiertos
```

---

## 👤 Usuarios y permisos

```bash
sudo su                        # entrar como root
su usuario                     # cambiar de usuario
passwd                         # cambiar contraseña propia
sudo passwd usuario            # cambiar contraseña de otro usuario
chmod 755 archivo              # cambiar permisos
chown usuario:grupo archivo    # cambiar dueño
```

---

## 📝 Editar archivos desde terminal

```bash
nano archivo.txt               # editor simple (recomendado)
# Guardar en nano: Ctrl+O → Enter | Salir: Ctrl+X

gedit archivo.txt              # editor gráfico (como bloc de notas)
cat archivo.txt                # mostrar contenido
less archivo.txt               # ver contenido con scroll (q para salir)
head -n 20 archivo.txt         # primeras 20 líneas
tail -n 20 archivo.txt         # últimas 20 líneas
tail -f archivo.log            # seguir un log en tiempo real
```

---

## 🔄 Servicios (systemd)

```bash
sudo systemctl status servicio     # ver estado
sudo systemctl start servicio      # iniciar
sudo systemctl stop servicio       # detener
sudo systemctl restart servicio    # reiniciar
sudo systemctl enable servicio     # activar al inicio
sudo systemctl disable servicio    # desactivar al inicio
```

---

## 💡 Tips útiles

- `Tab` → autocompleta comandos y rutas
- `↑ / ↓` → navegar historial de comandos
- `Ctrl + C` → cancelar comando en ejecución
- `Ctrl + L` → limpiar pantalla (o escribí `clear`)
- `Ctrl + R` → buscar en el historial
- `comando --help` → ver ayuda rápida
- `man comando` → manual completo del comando

---

_Ver también: [[03_Atajos]] | [[04_Troubleshooting]]_