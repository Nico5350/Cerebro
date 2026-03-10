#  Personalización

#mint #temas #personalizacion

> Cómo personalizar el aspecto y comportamiento de Linux Mint / Cinnamon.

---

## 🖌️ Temas, iconos y cursores

### Desde el panel de control

- Menú → Preferencias → **Temas**
- O desde terminal: `cinnamon-settings themes`

### Instalar temas desde terminal

```bash
# Temas GTK → van en:
~/.themes/

# Iconos → van en:
~/.icons/

# Cursores → van en:
~/.icons/  (misma carpeta)
```

### Temas populares recomendados

|Tema|Estilo|Dónde conseguirlo|
|---|---|---|
|`Mint-Y`|Moderno, minimalista (incluido)|preinstalado|
|`Dracula`|Oscuro, morado|dracula.theme|
|`Nordic`|Azul frío oscuro|gnome-look.org|
|`WhiteSur`|Estilo macOS|gnome-look.org|
|`Orchis`|Material Design colorido|gnome-look.org|

### Iconos populares

|Pack|Estilo|
|---|---|
|`Papirus`|Flat, muy completo|
|`Numix Circle`|Circular colorido|
|`Tela`|Minimalista|

```bash
sudo apt install papirus-icon-theme    # instalar Papirus
```

---

## 🖥️ Panel y barra de tareas

### Editar el panel

- Click derecho en el panel → **Configuración del panel**
- Podés mover el panel a cualquier lado (arriba, abajo, izquierda, derecha)

### Agregar / quitar applets del panel

- Click derecho en el panel → **Añadir applets al panel**
- O: `cinnamon-settings applets`

### Applets útiles

|Applet|Función|
|---|---|
|`System Monitor`|CPU/RAM en el panel|
|`Weather`|Clima en la barra|
|`Cinnamenu`|Menú mejorado|
|`Clipboard Manager`|Historial del portapapeles|
|`Calendar`|Calendario desplegable|

---

## 🌅 Fondo de pantalla

```bash
# Cambiar fondo desde terminal:
gsettings set org.cinnamon.desktop.background picture-uri "file:///ruta/imagen.jpg"

# O abrir el configurador:
cinnamon-settings backgrounds
```

### Fondos dinámicos / slideshow

- Cinnamon soporta slideshows nativamente
- Menú → Preferencias → Fondo de escritorio → seleccionar carpeta

---

## ✨ Efectos y animaciones

```bash
cinnamon-settings effects       # activar/desactivar efectos de ventanas
```

- Para equipos lentos: desactivar efectos mejora el rendimiento
- Para equipos potentes: activar efectos como "Magia del escritorio"

---

## 🔲 Extensiones de Cinnamon

```bash
cinnamon-settings extensions
```

Extensiones útiles:

|Extensión|Función|
|---|---|
|`Transparent panels`|Panel con transparencia|
|`Coverflow Alt-Tab`|Alt+Tab visual estilo carátulas|
|`Scale`|Vista general de todas las ventanas|
|`Expo`|Miniaturas de espacios de trabajo|

---

## 🖱️ Dock / Barra de lanzamiento

### Plank (dock estilo macOS)

```bash
sudo apt install plank
plank &                          # iniciar
plank --preferences              # configurar
```

Para que inicie automáticamente:

- Menú → Preferencias → **Aplicaciones al inicio** → Agregar → `plank`

### Cairo-Dock

```bash
sudo apt install cairo-dock cairo-dock-plug-ins
```

---

## 🔤 Fuentes

```bash
# Instalar fuentes personalizadas:
# Copiar archivos .ttf o .otf a:
~/.fonts/
# O crear la carpeta si no existe:
mkdir ~/.fonts
cp MiFuente.ttf ~/.fonts/
fc-cache -fv              # actualizar caché de fuentes
```

### Fuentes recomendadas para programación

|Fuente|Descripción|
|---|---|
|`JetBrains Mono`|Clara, con ligaduras|
|`Fira Code`|Con ligaduras de código|
|`Hack`|Diseñada para terminales|

```bash
sudo apt install fonts-firacode fonts-hack
```

### Cambiar fuente del sistema

```bash
cinnamon-settings fonts
```

---

## 🌙 Tema oscuro del sistema

```bash
# Activar tema oscuro global:
gsettings set org.cinnamon.desktop.interface gtk-theme "Mint-Y-Dark"
gsettings set org.cinnamon.desktop.interface icon-theme "Mint-Y-Dark"

# Desde la interfaz:
cinnamon-settings themes
```

---

## 🔧 Tweaks avanzados con dconf

```bash
dconf-editor          # interfaz gráfica (sudo apt install dconf-editor)

# Ejemplos de cambios por terminal:
gsettings list-schemas | grep cinnamon       # ver esquemas disponibles
gsettings list-keys org.cinnamon.desktop.interface   # ver claves
```

---

_Ver también: [[03_Atajos]] | [[05_Apps]]_