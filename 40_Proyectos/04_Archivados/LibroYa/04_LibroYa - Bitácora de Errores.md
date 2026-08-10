---
tipo: bitacora_errores
---
# 🐛 Bitácora de Errores

| Fecha | Error | Solución / Estado |
| :--- | :--- | :--- |
| 2026-03-10 | CORS bloqueado por `allow_credentials` | Pendiente de refactorización en `main.py` |
| 2026-03-10 | Cúspide devuelve 403 Forbidden | Implementar rotación de headers |

---
## Sesión de desarrollo — 10 de marzo de 2026

### Resumen de Cambios Técnicos

En esta sesión se priorizó la robustez del motor de scraping y la seguridad de la API, resolviendo bloqueos críticos de infraestructura y de renderizado dinámico en tiendas específicas.

> [!SUCCESS] Problema 1: Seguridad anti-bloqueo en scrapers (RESUELTO) Se implementó una capa de invisibilidad en `backend/scrapers/base.py` para evitar detecciones por comportamiento automatizado.
> 
> - **Rotación de Identidad:** Pool de 7 User-Agents reales (Chrome, Firefox, Safari, Edge) que se reconstruyen en cada request.
>     
> - **Simulación Humana:** Delays aleatorios obligatorios entre `SCRAPER_DELAY_MIN` (1.0s) y `SCRAPER_DELAY_MAX` (3.0s) antes de cada petición.
>     
> - **Gestión de Reintentos:** Sistema inteligente con backoff lineal para errores 429 (5s/10s/15s) y reintento inmediato para timeouts.
>     

> [!SUCCESS] Problema 2: Estándares CORS y Modernización de FastAPI (RESUELTO) Limpieza de deuda técnica en `backend/main.py` para cumplir con los estándares de seguridad modernos.
> 
> - **CORS Seguro:** Se eliminó la configuración inválida de `allow_origins=["*"]`. Ahora los dominios se gestionan vía `CORS_ORIGINS` en el `.env`.
>     
> - **Lifespan Manager:** Migración total de los eventos `startup/shutdown` (deprecados) al nuevo estándar de `lifespan context manager` de FastAPI.
>     
> - **Restricción de Métodos:** API limitada estrictamente a `GET` para reducir la superficie de ataque.
>     

> [!SUCCESS] Problema 3: Scraper de Cúspide (Motor Playwright) (RESUELTO) Finalización del scraper para `cuspide.com.ar` superando el bloqueo de renderizado por JavaScript.
> 
> - **Desafío Técnico:** El sitio usa WooCommerce con renderizado dinámico; el HTML estático estaba vacío.
>     
> - **Solución:** Implementación de **Playwright con Chromium headless** para ejecutar el JS y capturar selectores reales como `div.box-text-products`.
>     
> - **Optimización de Performance:** Bloqueo selectivo de carga de imágenes y fuentes para acelerar el proceso de scraping.
>     

---

### 🛠️ Infraestructura y Configuración

Se estandarizó el entorno de desarrollo mediante la creación de archivos de control de versiones y variables de entorno.

> [!NOTE] Gestión de Entorno Se han creado los archivos `.env` y `.env.example` para desacoplar la configuración del código fuente. Se configuró `.gitignore` para proteger la base de datos `libroya.db` y las claves del entorno.

**Variables de Entorno Actuales (`backend/.env`):** | Variable | Valor | Descripción | | :--- | :--- | :--- | | `DB_PATH` | `./libroya.db` | Ruta local de la base SQLite. | | `CORS_ORIGINS` | `localhost:3000, ...` | Orígenes permitidos para el frontend. | | `SCRAPER_DELAY_MIN` | `1.0` | Delay mínimo para evitar baneos. | | `SCRAPER_MAX_RETRIES`| `3` | Límite de reintentos por scraper. |

---

### ⚠️ Backlog Actualizado (Pendientes)

> [!WARNING] Próximos Desafíos
> 
> - [ ] **Problema 4:** Implementar scraper para Yenny/El Ateneo (verificar si requiere Playwright).
> - [ ] **Problema 5:**  Arreglar scraper de mercado libre(.
>     
> - [ ] **Problema 6:** Sistema de feedback de errores (el frontend debe notificar qué tiendas fallaron).
>     
> - [ ] **Seguridad:** Implementar Rate Limiting en la API para prevenir abusos de terceros.
>     
> - [ ] **Producción:** Configurar variables de entorno específicas para el despliegue con dominios reales.
>