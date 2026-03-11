---
tipo: documentacion_tecnica
stack: [Python, FastAPI, SQLite]
---
# 🐍 Lógica de Scraping y API

> [!NOTE] Arquitectura Asíncrona
> Se utiliza `asyncio.gather()` para disparar las peticiones en paralelo, reduciendo el tiempo de espera total al del scraper más lento.

### 📋 Contrato del Scraper (`BaseScraper`)
Todos los scrapers deben heredar de esta clase e implementar:
- `search(query, category)`: Retorna una lista de objetos `ScrapedBook`.
- Uso de `httpx.AsyncClient` para manejo de sesiones.

### 🗄️ Gestión de Base de Datos
- **Caché:** TTL de 30 minutos definido en `search_cache`.
- **Deduplicación:** Se basa en el **ISBN** (si está disponible) o en similitud de texto (0.65).