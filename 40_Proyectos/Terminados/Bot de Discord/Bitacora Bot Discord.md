---
tipo: bitacora_sysadmin
materia_o_proyecto: Bot Discord
tags:
  - server
importancia: Terminado
fecha_creacion: 2026-02-11 16:24
prioridad:
  - Terminado
---
# 📜 Bitácora: Bot Discord
[[Índice de Proyectos Terminados]]

> [!ABSTRACT] Resumen del Cambio
> 3-errores encontrados
> -  No iniciaba el servidor de cobbleverse ni atm10
> - Al no haber ningún servidor conectado devolvía una tabla vacía
> -  El comando !Stop no funcionaba
> 1 mejora de interfaz
> - Se cambiaron algunos textos par que se entiendan mejor
> -
## ⚠️ Problemas Encontrados y Solución
> 1 - Para resolver el primer problema se tuvo que:
> en primer lugar reenombrar archivos que eran incompatibles, tambien se cambio el codigo de bot.py 

## 🚀 Comandos Utilizados
```bash
# Pimport discord
from discord.ext import commands
import subprocess
import os
import asyncio

# --- CONFIGURACIÓN --- 

# IDs de Discord
ALLOWED_USERS = [123456789012345678, 987654321098765432, 337022736054616074, 342091082277847043, 327627678163140628]
SCRIPT_PATH = "/scripts"
# ---------------------

intents = discord.Intents.default()
intents.message_content = True
bot = commands.Bot(command_prefix='!', intents=intents)

def is_allowed(ctx):
    return ctx.author.id in ALLOWED_USERS

# Función silenciosa (Solo devuelve texto si hay ERROR)
def run_system_command_silent(cmd_list):
    try:
        result = subprocess.run(
            cmd_list, 
            stdout=subprocess.PIPE,
            stderr=subprocess.STDOUT,
            text=True, 
            timeout=120
        )
        # Si el script termina bien (exit code 0), no devolvemos nada (silencio)
        if result.returncode == 0:
            return None 
        # Si falló, devolvemos el error
        return result.stdout[-1900:]
    except subprocess.TimeoutExpired:
        return "⚠️ El proceso tardó demasiado, pero sigue corriendo en segundo plano."
    except Exception as e:
        return f"Error crítico: {str(e)}"

@bot.event
async def on_ready():
    print(f'Bot conectado y limpio: {bot.user}')
    await bot.change_presence(activity=discord.Game(name="Minecraft"))

# --- COMANDOS MINIMALISTAS ---

@bot.command()
@commands.cooldown(1, 30, commands.BucketType.guild)
@commands.check(is_allowed)
async def cobble(ctx):
    # Mensaje 1: Aviso de inicio
    await ctx.send("🚀 **Iniciando Cobbleverse...**")
    
    # Ejecutamos en silencio
    error_msg = await asyncio.to_thread(run_system_command_silent, ["bash", f"{SCRIPT_PATH}/jugar_cobbleverse.sh"])
    
    if error_msg:
        # Solo mostramos mensaje si hubo error
        await ctx.send(f"⚠️ **Ocurrió un problema:**\n```\n{error_msg}\n```")
    else:
        # Mensaje de éxito limpio
        await ctx.send("✅ **Cobbleverse está ACTIVO.**")

@bot.command()
@commands.cooldown(1, 30, commands.BucketType.guild)
@commands.check(is_allowed)
async def atm(ctx):
    await ctx.send("**Iniciando All The Mods 10...**")
    
    error_msg = await asyncio.to_thread(run_system_command_silent, ["bash", f"{SCRIPT_PATH}/jugar-atm.sh"])
    
    if error_msg:
        await ctx.send(f"⚠️ **Ocurrió un problema:**\n```\n{error_msg}\n```")
    else:
        await ctx.send("✅ **ATM 10 está ACTIVO.**")

@bot.command()
@commands.cooldown(1, 10, commands.BucketType.guild)
@commands.check(is_allowed)
async def stop(ctx):
    await ctx.send("**Apagando servidores...**")
    
    await asyncio.to_thread(run_system_command_silent, ["bash", f"{SCRIPT_PATH}/stop-all.sh"])
    
    await ctx.send("**Todo apagado.**")

@bot.command()
@commands.check(is_allowed)
async def status(ctx):
    # El status sí lo dejamos con un poco más de info, pero limpia
    def get_status():
        res = subprocess.run(["docker", "ps", "--format", "table {{.Names}}\t{{.Status}}"], capture_output=True, text=True)
        lines = res.stdout.split('\n')
        filtered = [line for line in lines if "cobbleverse" in line or "atm10" in line or "NAMES" in line]
        
        if len(filtered) > 1:
            return "```\n" + "\n".join(filtered) + "\n```"
        else:
            return "**Todo desconectado.**"
    
    msg = await asyncio.to_thread(get_status)
    await ctx.send(msg)

# Manejo de errores de Discord (Cooldowns y Permisos)
@bot.event
async def on_command_error(ctx, error):
    if isinstance(error, commands.CheckFailure):
        await ctx.send("⛔ Sin permiso.")
    elif isinstance(error, commands.CommandOnCooldown):
        # Mensaje más corto para el cooldown
        await ctx.send(f"⏳ Espera {int(error.retry_after)}s.")
    else:
        print(f"Error: {error}")

bot.run(TOKEN)

---------------------------------------------------------------------
(Script de Cobbleverse)
#!/bin/bash
echo "ðŸ›‘ Deteniendo ATM10..."
docker stop atm10

echo "ðŸš€ Iniciando Cobbleverse..."
docker start cobbleverse

echo "âœ… Servidor arrancando..."
echo "ðŸ“œ Mostrando terminal si hay algun error"
docker logs -f cobbleverse
---------------------------------------------------------------------
(Script de ATM)
!/bin/bash
echo "ðŸ›‘ Deteniendo Cobbleverse..."
docker stop cobbleverse

echo "ðŸš€ Iniciando All The Mods 10 ..."
docker start atm10

echo "âœ… Servidor arrancando..."
echo "Mostrara en consola si hay algun error"
sleep 2
docker logs -f atm10

```

[[Inidice de Bitacoras]]]
