# 🗃️ Obsidian + Git — Guía de configuración

#git #obsidian #config

> Sincronizar la bóveda entre Linux Mint y Windows usando GitHub + plugin Obsidian Git.

---

## 📋 Requisitos previos

- Cuenta en GitHub ✅
- Git instalado en Linux y Windows
- Plugin **Obsidian Git** instalado en Obsidian

---

## 🐧 PARTE 1 — Configuración en Linux Mint

### 1. Instalar Git

```bash
sudo apt install git
git --version    # verificar instalación
```

### 2. Configurar identidad

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

### 3. Crear token en GitHub

1. GitHub → tu foto de perfil → **Settings**
2. Bajar hasta **Developer settings** → **Personal access tokens** → **Tokens (classic)**
3. **Generate new token (classic)**
4. Nombre: `obsidian-boveda`
5. Expiración: `No expiration` (o la que prefieras)
6. Scopes: tildar **repo** (todo el bloque)
7. **Generate token** → ⚠️ COPIARLO AHORA, no se vuelve a mostrar

### 4. Crear repositorio en GitHub

1. GitHub → **New repository**
2. Nombre: `mi-boveda` (o el que quieras)
3. Visibilidad: **Private** ← importante
4. **NO** inicializar con README
5. Crear repositorio → copiar la URL (formato: `https://github.com/usuario/mi-boveda.git`)

### 5. Inicializar Git en la bóveda

```bash
# Ir a la carpeta de tu bóveda (en la partición Windows)
cd /media/TU_USUARIO/Windows/ruta/a/tu/boveda
# O donde tengas la bóveda en Linux

git init
git add .
git commit -m "primer commit - boveda inicial"
git branch -M main
git remote add origin https://github.com/TUUSUARIO/mi-boveda.git
git push -u origin main
```

> Si pide contraseña, usá el **token** que copiaste (no tu contraseña de GitHub)

### 6. Guardar credenciales para no pedirlas siempre

```bash
git config --global credential.helper store
# La próxima vez que hagas push/pull, las guarda automáticamente
```

---

## 🪟 PARTE 2 — Configuración en Windows

### 1. Instalar Git para Windows

- Descargar desde: https://git-scm.com/download/win
- Instalación por defecto está bien

### 2. Configurar identidad (en Git Bash o terminal)

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

### 3. Clonar la bóveda (si no la tenés ya)

```bash
git clone https://github.com/TUUSUARIO/mi-boveda.git C:\ruta\donde\quieras
```

> Si ya tenés la bóveda en Windows, hacé lo mismo que en Linux:  
> `git init` → `git remote add origin URL` → `git pull origin main`

---

# 4. Utilizar una Branch

```
# Guardar los cambios
git add .
git commit -m "Añadida nueva mecánica al Tower Defense"
#Pushear a la rama
git push -u "Rama"


# 2. Vuelve a la rama principal (suele llamarse main o master)
git switch main

# 3. Descarga las novedades que hayan subido tus compañeros (CRÍTICO)
git pull origin main

# 4. Fusiona tu rama de pruebas hacia la principal
git merge implementacion-recursos

# 5. Sube el juego actualizado con todos los cambios integrados
git push origin main
```

---

## 🙈 Archivo .gitignore recomendado

Creá un archivo `.gitignore` en la raíz de tu bóveda:

```
# Archivos del sistema
.trash/
.DS_Store
Thumbs.db

# Workspace local (no compartir entre sistemas)
.obsidian/workspace.json
.obsidian/workspace-mobile.json

# Caché
.obsidian/cache
```

> ⚠️ NO ignorar `.obsidian/plugins/` ni `.obsidian/themes/` — ahí están los iconos y plugins

---

## 🚨 Solución de conflictos

Si al hacer pull hay conflictos (editaste en los dos sistemas sin sincronizar):

```bash
# Ver qué archivos tienen conflicto
git status

# Abrir el archivo con conflicto, buscar estas marcas:
# <<<<<<< HEAD
# (tu versión)
# =======
# (versión remota)
# >>>>>>> origin/main

# Editá el archivo dejando la versión correcta y borrá las marcas
# Luego:
git add archivo-resuelto.md
git commit -m "resolver conflicto"
git push
```

---

## ✅ Verificar que todo funciona

```bash
git status          # ver estado actual
git log --oneline   # ver historial de commits
git remote -v       # ver repositorio remoto configurado
```

---

_Ver también: [[00_Inicio]] | [[02_Configuraciones]]_