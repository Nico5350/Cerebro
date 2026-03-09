# 🎮 Infraestructura Minecraft Dual (Docker)

**Estado:** 🟢 Operativo
**Servidor Host:** `192.168.0.6` (Ubuntu Server)
**Gestión:** Docker + Scripts Bash
**Restricción Crítica:**  NUNCA encender ambos servidores simultáneamente.

---
## Conectado a estos servidores:
- [[ATM 10 Lite]]
-  [[Cobbleverse]]
##  Arquitectura del Sistema

El sistema utiliza **dos contenedores** separados que comparten el hardware pero usan puertos distintos. La gestión de RAM se controla vía scripts que apagan uno antes de encender el otro.

```mermaid
graph TD
    User((Jugador)) -->|Túnel 1| Playit_Cobble[Playit.gg: Cobbleverse]
    User -->|Túnel 2| Playit_ATM[Playit.gg: ATM10]
    
    Playit_Cobble -->|Port 25565| Docker_Cobble[Contenedor: cobbleverse]
    Playit_ATM -->|Port 25566| Docker_ATM[Contenedor: atm10]
    
    subgraph "Server (6.7GB RAM)"
    Docker_Cobble
    Docker_ATM
    end
    
    style Docker_Cobble fill:#f9f,stroke:#333,stroke-width:2px
    style Docker_ATM fill:#bbf,stroke:#333,stroke-width:2px
```
## Comandos basicos
> [!INFO] Comandos
> jugar-atm.sh
> jugar-cobbleverse.sh
> stop-all.sh