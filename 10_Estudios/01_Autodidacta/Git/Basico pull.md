# 🚀 Guía de Git: Iniciar Proyecto y Configurar SSH

## 1. Descargar (Clonar) un proyecto desde cero
Si es la primera vez que configuras

git clone <URL-DEL-REPOSITORIO>
cd <nombre-de-la-carpeta-del-proyecto>

Si el proyecto ya está clonado pero necesitas traer los últimos cambios del servidor:

#git pull origin main

## 2. Flujo básico de trabajo (Guardar y Subir)
Los tres comandos del día a día para confirmar tus cambios

git add .
git commit -m "Descripción clara de lo que modificaste"
git push

## 3. Configurar llave SSH (Para omitir la contraseña)
La forma más cómoda y segura de evitar que Git pida credenciales constantemente es configurando una clave SSH directamente en tu terminal.

**Paso A: Generar la clave**
Abre tu terminal y ejecuta:
Utilizar el mail del github
ssh-keygen -t ed25519 -C "tu_correo@ejemplo.com"

*(Presiona Enter a todo para dejar los valores por defecto. Cuando pida "passphrase", puedes presionar Enter de nuevo para dejarlo en blanco).*

**Paso B: Iniciar el agente y añadir la clave**
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

**Paso C: Añadir la clave a la plataforma (GitHub/GitLab)**
Muestra tu clave pública en la terminal con este comando:

cat ~/.ssh/id_ed25519.pub

Copia el texto que aparece en pantalla. Luego, anda a la configuración de tu cuenta en la plataforma donde alojan el código (ej. Settings > SSH and GPG keys), hace click en "New SSH key" y pega el texto.

**Paso D: Asegurar que el repositorio usa SSH**
Para que la llave funcione, Git debe conectarse por SSH y no por HTTPS. Ejecuta esto dentro de la carpeta de tu proyecto:

git remote set-url origin git@github.com:Usuario/repositorio-juego.git

*(Asegúrate de reemplazar la URL final por la dirección SSH real de tu repositorio, la cual encuentras en el botón "Code" o "Clone" de la página web).*