# Captura de Sueño — Yanbal

## Stack
- HTML semántico + Tailwind CSS (via CDN: `https://cdn.tailwindcss.com`)
- Vanilla JS (sin frameworks)
- Mobile-first, viewport fijo `360×700px`

## Fuente
Maison Neue (archivos locales en `ui_resources/Maison Neue/`)
- Peso 400 → `MaisonNeue-Book.otf`
- Peso 600 → `MaisonNeue-Demi.otf`
- **Nunca usar otra fuente ni peso distinto**

## Assets
- `ui_resources/ilustrations/` — ilustraciones de cada pantalla
- `ui_resources/Maison Neue/` — archivos de fuente `.otf`
- `ui_resources/Icons/` — íconos
- `ui_resources/BPLAN/` — imágenes del plan de negocio

## Documentación — leer SIEMPRE antes de tocar código
| Archivo | Cuándo leerlo |
|---|---|
| `docs/estandar_desarrollo_ui.md` | Antes de crear o modificar cualquier pantalla |
| `docs/flujo_sueno_bp.md` | Antes de implementar lógica de campos o navegación |
| `docs/figma_screens_index.md` | Para obtener el node-id de Figma de cada pantalla |

## Reglas obligatorias

### Layout
- Cada pantalla tiene exactamente 2 zonas internas: contenido (flex-1, padding 24px) + footer con botón (92px fijo abajo)
- Margen mínimo de 24px en todos los bordes del contenido — ningún elemento toca el borde
- El contenedor de cada step es `w-full max-w-[360px] min-h-[calc(100vh-8px)]`
- **Nunca** usar `w-[360px]` fijo — siempre `w-full max-w-[360px]` para que sea responsive en pantallas pequeñas
- `body`: `bg-white min-h-screen flex flex-col items-center` — centrado horizontal, sin color de fondo contrastante para evitar contorno visible alrededor del contenedor
- El contenido dentro de cada step también debe estar centrado horizontalmente: `flex flex-col items-center` en la zona de contenido, con `max-w-[312px]` en los elementos de texto

### Barra de progreso
- **Una sola barra global**, fuera de los steps: `<div class="fixed top-0 left-0 w-full h-2 z-50">` con `id="global-progress"`
- Ocupa el 100% del ancho del viewport — no está confinada al contenedor de 360px
- Track: `#f9c7b6` | Fill: `#c94e22` | Altura: 8px
- Se actualiza en `goToStep()` vía `document.getElementById('global-progress').style.width = pct + '%'`
- Añadir un espaciador `<div class="w-full h-2">` inmediatamente después para compensar el `fixed`
- **Nunca** poner barras de progreso individuales dentro de cada step

### Colores
- Solo usar los tokens definidos en `docs/estandar_desarrollo_ui.md`
- Nunca hardcodear colores hex directamente en componentes
- Color primario: `#c94e22` (Yanbal Orange 80)

### Botón CTA
- Siempre deshabilitado al entrar a pantallas de captura (3, 4, 5, 6, 8, 9)
- Siempre activo en pantallas de intro/celebración (0, 1, 2, 7, 10)
- Ancho fijo: 312px (360px - 24px × 2)
- Border-radius: 999px (pill)

### Figma
- Para cada pantalla, llamar a `get_design_context` con el node-id del índice antes de escribir código
- No interpretar el diseño de memoria — siempre leer desde Figma

## Flujo para desarrollar una pantalla nueva

Cuando el usuario pida desarrollar cualquier pantalla, seguir este orden sin excepción:

```
1. Leer \Documentos\Claude Code Projects\Captura de Sueño/figma_screens_index.md → buscar el node-id de esa pantalla
2. Leer \Documentos\Claude Code Projects\Captura de Sueño/estandar_desarrollo_ui.md → reglas de layout, colores y componentes
3. Leer "D:\Users\Olama\OneDrive - UNIQUEYANBAL\Documentos\Claude Code Projects\Captura de Sueño\context\VALIDACION_FLUJO_SUENO.md" → lógica, campos y reglas de negocio de esa pantalla
4. Llamar a get_design_context con el node-id encontrado en el paso 1
5. Implementar el HTML respetando la estructura de 3 zonas
6. Verificar el checklist de docs/estandar_desarrollo_ui.md sección 14
```

**El usuario solo necesita decir:** `"Desarrolla la pantalla 3"` o `"Desarrolla 03_sueno_texto.html"`  
Claude Code debe resolver el node-id leyendo el índice — no pedirlo al usuario.

Cada pantalla se trabaja en el mismo archivo, ya que todo es parte de un único flujo.