---
tipo: documentacion_tecnica
stack: [Next.js, TypeScript, Tailwind]
---
# ⚛️ Frontend LibroYa

### 🎨 Componentes Clave
- `SearchBar`: Maneja el estado de la búsqueda y debounce.
- `BookCard`: Renderiza la comparativa de precios. Resalta el `best_price` con color verde.

### 📡 Consumo de API
La función `fetchBooks` en `lib/api.ts` centraliza las llamadas:
- Endpoint: `/api/v1/search`
- Manejo de estados: `loading`, `error`, `results`.