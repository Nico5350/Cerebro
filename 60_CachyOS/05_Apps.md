# 📦 Apps y Herramientas Útiles

#mint #app

> Aplicaciones recomendadas para Linux Mint, organizadas por categoría.  
> Instalación básica: `sudo apt install nombre-app`

---

## 🛠️ Sistema y utilidades

|App|Descripción|Instalación|
|---|---|---|
|`htop`|Monitor del sistema interactivo|`sudo apt install htop`|
|`neofetch`|Info del sistema en terminal (estético)|`sudo apt install neofetch`|
|`timeshift`|Snapshots y restauración del sistema|`sudo apt install timeshift`|
|`bleachbit`|Limpiador de archivos temporales|`sudo apt install bleachbit`|
|`stacer`|Optimizador y monitor gráfico|`sudo apt install stacer`|
|`gparted`|Gestor de particiones gráfico|`sudo apt install gparted`|
|`dconf-editor`|Editor avanzado de configuraciones|`sudo apt install dconf-editor`|

---

## 📁 Gestión de archivos

|App|Descripción|Instalación|
|---|---|---|
|`nemo`|Gestor de archivos (ya incluido)|preinstalado|
|`double-commander`|Gestor de archivos doble panel|`sudo apt install doublecmd-gtk`|
|`ranger`|Gestor de archivos en terminal|`sudo apt install ranger`|
|`7zip`|Compresor de archivos|`sudo apt install 7zip`|
|`meld`|Comparador visual de archivos|`sudo apt install meld`|

---

## 🌐 Internet y comunicación

|App|Descripción|Instalación|
|---|---|---|
|`firefox`|Navegador web (preinstalado)|preinstalado|
|`thunderbird`|Cliente de correo|`sudo apt install thunderbird`|
|`telegram-desktop`|Mensajería|`sudo apt install telegram-desktop`|
|`filezilla`|Cliente FTP/SFTP|`sudo apt install filezilla`|
|`transmission`|Cliente BitTorrent|`sudo apt install transmission`|
|`qbittorrent`|Cliente BitTorrent alternativo|`sudo apt install qbittorrent`|

---

## 📝 Oficina y productividad

|App|Descripción|Instalación|
|---|---|---|
|`libreoffice`|Suite ofimática completa|`sudo apt install libreoffice`|
|`obsidian`|Notas en Markdown con links|Descargar .deb desde obsidian.md|
|`cherrytree`|Notas con estructura de árbol|`sudo apt install cherrytree`|
|`zathura`|Lector de PDF ligero|`sudo apt install zathura`|
|`evince`|Lector PDF (preinstalado)|preinstalado|
|`flameshot`|Capturas de pantalla avanzadas|`sudo apt install flameshot`|
|`xclip`|Copiar salida de terminal al portapapeles|`sudo apt install xclip`|

---

## 🎨 Multimedia

|App|Descripción|Instalación|
|---|---|---|
|`vlc`|Reproductor multimedia completo|`sudo apt install vlc`|
|`mpv`|Reproductor multimedia ligero|`sudo apt install mpv`|
|`gimp`|Editor de imágenes|`sudo apt install gimp`|
|`inkscape`|Editor de vectores SVG|`sudo apt install inkscape`|
|`kdenlive`|Editor de video|`sudo apt install kdenlive`|
|`audacity`|Editor de audio|`sudo apt install audacity`|
|`obs-studio`|Grabación y streaming|`sudo apt install obs-studio`|

---

## 💻 Desarrollo

|App|Descripción|Instalación|
|---|---|---|
|`git`|Control de versiones|`sudo apt install git`|
|`vscode`|Editor de código|Descargar .deb desde code.visualstudio.com|
|`vim`|Editor terminal avanzado|`sudo apt install vim`|
|`nano`|Editor terminal simple|preinstalado|
|`curl`|Transferencia de datos por URL|`sudo apt install curl`|
|`wget`|Descargador de archivos|`sudo apt install wget`|
|`python3-pip`|Gestor de paquetes Python|`sudo apt install python3-pip`|
|`nodejs` + `npm`|JavaScript en servidor|`sudo apt install nodejs npm`|

---

## 🔒 Seguridad y privacidad

|App|Descripción|Instalación|
|---|---|---|
|`ufw`|Firewall sencillo|`sudo apt install ufw`|
|`gufw`|Interfaz gráfica para UFW|`sudo apt install gufw`|
|`keepassxc`|Gestor de contraseñas local|`sudo apt install keepassxc`|
|`gnupg`|Cifrado GPG|`sudo apt install gnupg`|
|`clamav`|Antivirus|`sudo apt install clamav`|

---

## 📦 Instalar apps en otros formatos

### Flatpak (apps universales, más actualizadas)

```bash
sudo apt install flatpak
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install flathub nombre.de.la.app
flatpak run nombre.de.la.app
```

### AppImage (ejecutable portátil)

```bash
chmod +x nombre-app.AppImage
./nombre-app.AppImage
```

### Archivo .deb descargado

```bash
sudo dpkg -i nombre-app.deb
sudo apt install -f              # resolver dependencias si hay errores
```

---

## 🔄 Actualizar / desinstalar Flatpaks

```bash
flatpak update                   # actualizar todas las apps Flatpak
flatpak uninstall nombre.app     # desinstalar
flatpak list                     # ver apps instaladas
```

---

_Ver también: [[02_Configuraciones]] | [[04_Troubleshooting]]_