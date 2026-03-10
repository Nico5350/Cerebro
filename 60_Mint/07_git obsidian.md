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

## 🔌 PARTE 3 — Plugin Obsidian Git

### Instalar el plugin

1. Obsidian → Configuración → Plugins de la comunidad
2. Buscar **Obsidian Git**
3. Instalar y **activar**
4. Hacer esto en **ambos sistemas**

### Configuración recomendada del plugin

|Opción|Valor recomendado|
|---|---|
|Auto backup interval|`10` minutos|
|Auto backup on file change|Activado|
|Auto pull interval|`10` minutos|
|Pull on startup|Activado ✅|
|Push on backup|Activado ✅|
|Commit message|`boveda: {{date}}`|

### Atajos útiles del plugin

|Atajo|Acción|
|---|---|
|`Ctrl + Shift + G`|Abrir panel de Git|
|Paleta de comandos → `Obsidian Git`|Ver todos los comandos|

---

## 🔄 Flujo de uso diario

```
Al abrir Obsidian → pull automático (baja cambios)
      ↓
   Trabajás normalmente
      ↓
Cada 10 min → commit + push automático
      ↓
Al abrir en el otro sistema → pull trae todo al día
```

### Si querés hacer push manual

- Paleta de comandos (`Ctrl + P`) → `Obsidian Git: Commit and push`

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