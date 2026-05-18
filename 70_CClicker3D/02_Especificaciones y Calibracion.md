
## 🔧 Especificaciones de la A1 Combo

|Característica|Detalle|
|---|---|
|Tecnología|FDM — Direct Drive|
|Área de impresión|256 × 256 × 256 mm|
|Velocidades|Hasta 500 mm/s (recomendado 250–350 mm/s)|
|Resolución de capa|0.05 – 0.35 mm|
|Temperatura nozzle|Hasta 300°C|
|Temperatura cama|Hasta 100°C|
|Sistema multicolor|AMS Lite (4 colores simultáneos)|
|Conectividad|WiFi + LAN|
|Consumo eléctrico|~280–320W en uso normal|
|Precio aprox.|USD 760 (A1 + AMS Combo)|

### Ventajas clave para negocio

- **Direct drive** = menos stringing, mejor con TPU y materiales flexibles
- **AMS Lite** = impresiones multicolor sin cambio manual = productos más atractivos
- **Calibración automática** = menos tiempo configurando, más tiempo produciendo
- **Bambu Studio** = slicing rápido con perfiles optimizados

---

## ⚙️ Calibración paso a paso

> **Regla de oro:** Calibrá cada vez que cambiés de marca de filamento o de material.

### 1. Calibración inicial (primer uso)

- [ ] Ejecutar **Full Calibration** desde Bambu Studio o pantalla táctil
- [ ] Incluye: vibration compensation + flow rate + bed leveling automático
- [ ] Duración: ~15 minutos
- [ ] Solo necesaria una vez (salvo reseteo de fábrica)

### 2. Nivelación de cama (bed leveling)

- [ ] Activar **Auto Bed Leveling** antes de cada sesión nueva
- [ ] La A1 hace mesh leveling de 49 puntos automáticamente
- [ ] Si la primera capa no adhiere bien → limpiar la cama con alcohol isopropílico
- [ ] Para PETG/ABS → usar laca o adhesivo sobre la cama

### 3. Calibración de flujo (flow rate)

```
Método:
1. Imprimir cubo de calibración de 20mm (sin relleno, 1 perímetro)
2. Medir las paredes con calibre digital
3. Paredes deben medir exactamente el diámetro del nozzle (0.4mm)
4. Si son más gruesas → bajar flow multiplier (ej: de 1.0 a 0.95)
5. Si son más delgadas → subir flow multiplier
```

### 4. Torre de temperatura

```
Temperaturas a probar por material:
- PLA:  190°C – 230°C (óptimo suele ser 210–220°C)
- PETG: 220°C – 250°C (óptimo suele ser 235–245°C)
- ABS:  230°C – 260°C
- TPU:  220°C – 240°C

Buscar la capa con:
✓ Mejor calidad superficial
✓ Sin stringing (hilos entre piezas)
✓ Sin underextrusion (huecos en la superficie)
```

### 5. Test de retracción (stringing)

```
Parámetros para direct drive (A1):
- Retraction distance: 0.5 – 1.5 mm (empezar en 1mm)
- Retraction speed: 30 – 45 mm/s
- Si hay stringing → aumentar retracción o bajar temperatura
- Imprimir modelo "stringing test" de Printables/MakerWorld
```

### 6. Calibración AMS Lite

- [ ] Ejecutar **Auto Color Calibration** desde el panel del AMS
- [ ] Verificar que los buffers no tengan tensión excesiva
- [ ] Asegurarse que las guías de filamento estén bien encajadas
- [ ] Con 4 colores distintos → hacer una purge tower adecuada en el slicer

### 7. Primera capa perfecta

```
La primera capa es TODO en impresión 3D.
- Live adjust Z durante la primera capa hasta lograr que el filamento
  "aplaste" levemente contra la cama
- No debe verse espacio entre líneas
- No debe quedar tan aplastada que se vea traslúcida
- Guardar el Z offset cuando lo tengas perfecto
```

---