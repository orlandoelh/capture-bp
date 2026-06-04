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
- Cada pantalla tiene exactamente 3 zonas: barra de progreso (8px) + contenido (flex-1, padding 24px) + footer con botón (92px fijo abajo)
- Margen mínimo de 24px en todos los bordes del contenido — ningún elemento toca el borde

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
1. Leer docs/figma_screens_index.md → buscar el node-id de esa pantalla
2. Leer docs/estandar_desarrollo_ui.md → reglas de layout, colores y componentes
3. Leer docs/flujo_sueno_bp.md → lógica, campos y reglas de negocio de esa pantalla
4. Llamar a get_design_context con el node-id encontrado en el paso 1
5. Implementar el HTML respetando la estructura de 3 zonas
6. Verificar el checklist de docs/estandar_desarrollo_ui.md sección 14
```

**El usuario solo necesita decir:** `"Desarrolla la pantalla 3"` o `"Desarrolla 03_sueno_texto.html"`  
Claude Code debe resolver el node-id leyendo el índice — no pedirlo al usuario.
