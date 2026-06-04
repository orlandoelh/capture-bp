# Estándar de Desarrollo UI — Captura de Sueño
## Yanbal · FrYDA Design System · HTML + Tailwind · Mobile-first

> **Regla de oro:** Todas las pantallas siguen la misma estructura de layout. Nunca hardcodear colores, tamaños de fuente ni espaciados fuera de los tokens definidos aquí.

---

## 1. Viewport y encuadre base

| Propiedad | Valor |
|---|---|
| Ancho de diseño en Figma | 360px |
| Alto de diseño en Figma | 700px |
| Dispositivo objetivo | Mobile (Android/iOS) |
| Desktop | No contemplado en esta versión |

### HTML base de cada pantalla

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0" />
  <title>Captura de Sueño</title>
  <link rel="stylesheet" href="../ui_resources/tokens.css" />
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-white font-maison antialiased">

  <!-- Pantalla: contenedor principal -->
  <div class="screen">
    <!-- 1. Barra de progreso (fija arriba) -->
    <!-- 2. Contenido scrolleable -->
    <!-- 3. Footer con botón (fijo abajo) -->
  </div>

</body>
</html>
```

---

## 2. Estructura de layout — 3 zonas fijas

Cada pantalla se divide en exactamente 3 zonas. Esta estructura NO varía entre pantallas.

```
┌──────────────────────────┐  ← 0px
│  [PROGRESS BAR]  8px     │  zona 1: fija arriba
├──────────────────────────┤  ← 8px
│                          │
│  [CONTENIDO]             │  zona 2: scrolleable, padding 24px
│  padding: 24px           │
│                          │
├──────────────────────────┤  ← height - 92px
│  [FOOTER + BOTÓN]  92px  │  zona 3: fija abajo
└──────────────────────────┘  ← 700px
```

### CSS de la estructura

```css
.screen {
  width: 360px;
  min-height: 700px;
  display: flex;
  flex-direction: column;
  position: relative;
  background: white;
  margin: 0 auto;
}

.screen-progress {
  /* Zona 1: barra de progreso */
  position: sticky;
  top: 0;
  width: 100%;
  height: 8px;
  z-index: 10;
}

.screen-content {
  /* Zona 2: contenido */
  flex: 1;
  padding: 24px;
  overflow-y: auto;
}

.screen-footer {
  /* Zona 3: footer con botón */
  position: sticky;
  bottom: 0;
  width: 100%;
  height: 92px;
  padding: 24px;
  background: white;
  border-top: 1px solid var(--fry-s-color-border-neutral-subtle);
  box-shadow: 0px -1px 4px 0px rgba(0, 0, 0, 0.10);
}
```

### En Tailwind

```html
<!-- Pantalla completa -->
<div class="w-[360px] min-h-[700px] flex flex-col mx-auto bg-white">

  <!-- Zona 1: barra de progreso -->
  <div class="sticky top-0 z-10 w-full h-2"><!-- ver sección 3 --></div>

  <!-- Zona 2: contenido -->
  <div class="flex-1 p-6 overflow-y-auto">
    <!-- contenido de la pantalla -->
  </div>

  <!-- Zona 3: footer -->
  <div class="sticky bottom-0 h-[92px] p-6 bg-white border-t border-[#e6e8ec] shadow-[0px_-1px_4px_0px_rgba(0,0,0,0.1)]">
    <!-- botón CTA -->
  </div>

</div>
```

---

## 3. Barra de progreso (zona 1)

Tomada directamente de Figma (node `1029:24308`).

- Alto: `8px`
- Track (fondo): `#f9c7b6` → `--fry-p-color-yanbal-orange-30`
- Fill (progreso): `#c94e22` → `--fry-p-color-yanbal-orange-80`
- El fill crece de izquierda a derecha según el paso actual

```html
<!-- Barra de progreso -->
<div class="w-full h-2 bg-[#f9c7b6] overflow-hidden">
  <div class="h-2 bg-[#c94e22] transition-all duration-300" style="width: 20%"></div>
  <!-- El % se calcula: (paso_actual / total_pasos) * 100 -->
</div>
```

**Cálculo del progreso:**

| Pantalla | Paso | % (de 10 pasos totales) |
|---|---|---|
| Intro | 0 | 0% |
| Antes de comenzar | 1 | 10% |
| Intro Sueño | 2 | 20% |
| Sueño: texto | 3 | 30% |
| Sueño: imagen | 4 | 40% |
| Sueño: costo | 5 | 50% |
| Sueño: campaña | 6 | 60% |
| Sueño: resultado | 7 | 70% |
| Motor: texto | 8 | 80% |
| Motor: imagen | 9 | 90% |
| Cierre | 10 | 100% |

---

## 4. Márgenes y espaciados

| Elemento | Valor | Token |
|---|---|---|
| Margen horizontal del contenido | `24px` | `p-6` en Tailwind |
| Margen vertical del contenido | `24px` | `p-6` en Tailwind |
| Gap entre elementos de contenido | `16px` | `gap-4` |
| Gap entre label y campo | `8px` | `gap-2` |
| Padding interno del footer | `24px` | `p-6` |

**Regla:** Todo el contenido visible respeta un margen mínimo de `24px` desde los bordes laterales de la pantalla. Nunca un elemento de texto o input toca el borde.

---

## 5. Botón CTA (zona 3)

Tomado de Figma (node `1029:24313`). Hay dos estados: **activo** y **deshabilitado**.

### Estructura HTML

```html
<!-- Estado deshabilitado (por defecto al entrar a la pantalla) -->
<button class="cta-button" disabled>
  Continuar
</button>

<!-- Estado activo (cuando el campo tiene valor) -->
<button class="cta-button cta-button--active">
  Continuar
</button>
```

### CSS del botón

```css
.cta-button {
  width: 312px;           /* 360px - 24px*2 de padding del footer */
  height: 44px;
  border-radius: 999px;   /* pill */
  font-family: "Maison Neue", sans-serif;
  font-size: 14px;
  font-weight: 600;       /* Demi */
  line-height: 20px;
  letter-spacing: 0.2px;
  text-align: center;
  cursor: not-allowed;
  
  /* Estado deshabilitado */
  background-color: #d2d2d4;   /* --fry-p-color-yanbal-black-30 */
  color: #a4a5a9;              /* neutral-40 */
  border: none;
}

.cta-button--active {
  background-color: #c94e22;   /* --fry-p-color-yanbal-orange-80 */
  color: white;
  cursor: pointer;
}

.cta-button--active:hover {
  background-color: #a83c18;   /* --fry-p-color-yanbal-orange-90 */
}

.cta-button--active:active {
  background-color: #7a2e14;   /* --fry-p-color-yanbal-orange-100 */
  transform: scale(0.98);
}
```

### En Tailwind

```html
<!-- Deshabilitado -->
<button disabled
  class="w-[312px] h-11 rounded-full bg-[#d2d2d4] text-[#a4a5a9] font-semibold text-sm leading-5 tracking-[0.2px] cursor-not-allowed">
  Continuar
</button>

<!-- Activo -->
<button
  class="w-[312px] h-11 rounded-full bg-[#c94e22] text-white font-semibold text-sm leading-5 tracking-[0.2px] cursor-pointer hover:bg-[#a83c18] active:bg-[#7a2e14] active:scale-[0.98] transition-all">
  Continuar
</button>
```

**Lógica de activación:** El botón pasa a activo solo cuando el campo requerido de esa pantalla tiene un valor. Se maneja con JS:

```javascript
// Patrón estándar para activar/desactivar el CTA
const input = document.getElementById('campo-requerido');
const btn = document.getElementById('btn-continuar');

function checkInput() {
  const hasValue = input.value.trim().length > 0;
  btn.disabled = !hasValue;
  btn.classList.toggle('cta-button--active', hasValue);
}

input.addEventListener('input', checkInput);
```

---

## 6. Botón "Regresar" (navegación secundaria)

Aparece en las pantallas de captura (no en intros ni celebraciones).

```html
<button class="flex items-center gap-1 text-sm font-normal text-[#1c1f28] leading-5">
  <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
    <path d="M12.5 15L7.5 10L12.5 5" stroke="#1c1f28" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
  </svg>
  Regresar
</button>
```

- Posición: parte superior izquierda del `.screen-content`, antes de cualquier ilustración
- No tiene fondo ni borde
- Color del texto e ícono: `#1c1f28` (yanbal-black-100)

---

## 7. Tipografía

**Fuente principal:** Maison Neue (local, desde `./fonts/`)  
**Solo dos pesos en uso:**

| Peso | Archivo | font-weight | Uso |
|---|---|---|---|
| Book | `MaisonNeue-Book.otf` | 400 | Cuerpo de texto, descripciones, labels |
| Demi | `MaisonNeue-Demi.otf` | 600 | Títulos, botones, valores destacados |

### Declaración @font-face (va en `tokens.css`)

```css
@font-face {
  font-family: "Maison Neue";
  src: url("../ui_resources/Maison Neue/MaisonNeue-Book.otf") format("opentype");
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}
@font-face {
  font-family: "Maison Neue";
  src: url("../ui_resources/Maison Neue/MaisonNeue-Demi.otf") format("opentype");
  font-weight: 600;
  font-style: normal;
  font-display: swap;
}
```

### Escala tipográfica en uso (pantallas de captura)

| Rol | Tamaño | Line-height | Peso | Clase CSS sugerida |
|---|---|---|---|---|
| Título de pantalla | 24px | 32px | 600 (Demi) | `.fry-heading-4` |
| Subtítulo / pregunta | 20px | 32px | 600 (Demi) | `.fry-heading-6` |
| Descripción / helper | 14px | 20px | 400 (Book) | `.fry-paragraph-14` |
| Label de input | 14px | 20px | 600 (Demi) | `.fry-label` |
| Texto de botón | 14px | 20px | 600 (Demi) | — (inline en botón) |
| Valor calculado destacado | 24px | 40px | 600 (Demi) | `.fry-price` |

```css
/* Clases listas para usar */
.fry-heading-4  { font-size: 24px; line-height: 32px; font-weight: 600; letter-spacing: 0.2px; }
.fry-heading-6  { font-size: 20px; line-height: 32px; font-weight: 600; letter-spacing: 0.2px; }
.fry-paragraph-14 { font-size: 14px; line-height: 20px; font-weight: 400; letter-spacing: 0.2px; }
.fry-label      { font-size: 14px; line-height: 20px; font-weight: 600; letter-spacing: 0.2px; }
.fry-price      { font-size: 24px; line-height: 40px; font-weight: 600; letter-spacing: 0.2px; }
```

---

## 8. Colores en uso

Solo se usan tokens semánticos (`--fry-s-*`). Nunca hex literales en el código de componentes.

| Rol | Token semántico | Hex | Uso |
|---|---|---|---|
| Acción primaria (botón activo) | `--fry-s-color-surface-action-primary` | `#c94e22` | Botón CTA activo, progreso fill |
| Acción primaria hover | — | `#a83c18` | Hover del botón activo |
| Acción primaria pressed | — | `#7a2e14` | Pressed del botón activo |
| Botón deshabilitado | `--fry-s-color-surface-interaction-empty-default` | `#d2d2d4` | Fondo botón inactivo |
| Texto deshabilitado | `--fry-s-color-content-disabled` | `#a4a5a9` | Texto botón inactivo |
| Progreso track | `--fry-p-color-yanbal-orange-30` | `#f9c7b6` | Fondo de la barra de progreso |
| Fondo de pantalla | `--fry-s-color-surface-default` | `#ffffff` | Fondo general |
| Texto primario | `--fry-s-color-content-primary` | `#1c1f28` | Títulos, texto principal |
| Texto secundario | `--fry-s-color-content-secondary` | `#575b66` | Descripciones, helpers |
| Borde sutil | `--fry-s-color-border-neutral-subtle` | `#e6e8ec` | Bordes de inputs, separadores |
| Borde activo (input focus) | `--fry-s-color-border-state-active-default` | `#c94e22` | Input con foco |

---

## 9. Inputs de texto y número

### Input de texto (pantallas 3 y 8)

```html
<textarea
  id="campo-sueno"
  placeholder="Escribe tu sueño aquí"
  rows="4"
  class="
    w-full
    rounded-lg
    border border-[#e6e8ec]
    px-4 py-3
    text-sm font-normal leading-5 tracking-[0.2px]
    text-[#1c1f28]
    placeholder:text-[#a4a5a9]
    resize-none
    outline-none
    focus:border-[#c94e22]
    transition-colors
  "
></textarea>
```

### Input numérico con moneda (pantalla 5)

```html
<div class="flex items-center w-full border border-[#e6e8ec] rounded-lg px-4 py-3 gap-2 focus-within:border-[#c94e22] transition-colors">
  <span class="text-sm font-normal text-[#575b66] shrink-0">S/</span>
  <input
    type="number"
    id="campo-costo"
    placeholder="0"
    class="flex-1 outline-none text-sm font-normal leading-5 tracking-[0.2px] text-[#1c1f28] placeholder:text-[#a4a5a9] bg-transparent"
  />
</div>
```

### Selector dropdown (pantalla 6)

```html
<div class="relative w-full">
  <select
    id="campo-campana"
    class="
      w-full appearance-none
      border border-[#e6e8ec] rounded-lg
      px-4 py-3
      text-sm font-normal leading-5 tracking-[0.2px]
      text-[#1c1f28]
      bg-white
      outline-none
      focus:border-[#c94e22]
      transition-colors
    "
  >
    <option value="" disabled selected>Campaña</option>
    <option value="3">C3</option>
    <!-- ... C4 a C13 -->
    <option value="13">C13</option>
  </select>
  <!-- Ícono chevron -->
  <svg class="absolute right-4 top-1/2 -translate-y-1/2 pointer-events-none" width="20" height="20" viewBox="0 0 20 20" fill="none">
    <path d="M5 7.5L10 12.5L15 7.5" stroke="#1c1f28" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
  </svg>
</div>
```

---

## 10. Grilla de selección de imágenes (pantallas 4 y 9)

```html
<div class="grid grid-cols-2 gap-3 w-full">
  <!-- Tarjeta de imagen -->
  <button
    class="image-card aspect-square rounded-xl border-2 border-transparent overflow-hidden bg-[#f5f3ef] transition-all"
    data-image-id="sueno-01"
    onclick="selectImage(this)"
  >
    <img src="../ui_resources/ilustrations/sueno-01.png" alt="Opción 1" class="w-full h-full object-cover" />
  </button>
  <!-- repetir x6 -->
</div>
```

```css
/* Estado seleccionado */
.image-card.selected {
  border-color: #c94e22;    /* --fry-p-color-yanbal-orange-80 */
  box-shadow: 0 0 0 2px #c94e22;
}
```

```javascript
function selectImage(el) {
  // Deseleccionar todas
  document.querySelectorAll('.image-card').forEach(c => c.classList.remove('selected'));
  // Seleccionar la actual
  el.classList.add('selected');
  // Activar el botón CTA
  document.getElementById('btn-continuar').disabled = false;
  document.getElementById('btn-continuar').classList.add('cta-button--active');
}
```

---

## 11. Ilustraciones

- Todas las ilustraciones viven en `./ui_resources/ilustrations/`
- Formato recomendado: `.png` o `.svg`
- Tamaño máximo en pantalla: `210×210px` (centrado, sin deformación)
- Siempre dentro de un contenedor con `max-width: 312px` (ancho del contenido)

```html
<!-- Contenedor de ilustración -->
<div class="flex justify-center items-center w-full mb-6">
  <img
    src="../ui_resources/ilustrations/nombre-ilustracion.png"
    alt=""
    aria-hidden="true"
    class="w-[210px] h-[210px] object-contain"
  />
</div>
```

---

## 12. Pantallas de celebración (transiciones)

Las pantallas 7 y 10 son de celebración/resultado, no de captura. Siguen la misma estructura de layout pero sin inputs. El área de contenido tiene:

- Ilustración centrada `210×210px`
- Título con el nombre de la participante: `font-size: 24px, font-weight: 600`
- Párrafo descriptivo: `font-size: 16px, font-weight: 400`
- Valor destacado (si aplica): `.fry-price` — `24px, 600`
- CTA activo por defecto (no requiere completar nada)

---

## 13. Estructura de archivos

Todo el flujo vive en **un solo archivo `index.html`**. No hay páginas separadas.

```
Captura de Sueño/
├── index.html          ← único archivo HTML, contiene los 11 pasos
├── CLAUDE.md
├── docs/
│   ├── estandar_desarrollo_ui.md
│   ├── flujo_sueno_bp.md
│   └── figma_screens_index.md
└── ui_resources/
    ├── Maison Neue/
    ├── ilustrations/
    └── Icons/
```

Cada paso (pantalla) es un `<div id="step-N">` dentro del `index.html`. La navegación entre pasos se maneja con JS puro — mostrando y ocultando divs, sin recargar la página ni cambiar de URL. Ver patrón de navegación en `docs/figma_screens_index.md`.

---

## 14. Checklist antes de entregar una pantalla

- [ ] Viewport meta tag incluido con `maximum-scale=1.0`
- [ ] Fuente Maison Neue cargando correctamente desde `./fonts/`
- [ ] Barra de progreso con el `%` correcto para esa pantalla
- [ ] Margen de `24px` en todos los bordes del contenido
- [ ] Botón CTA deshabilitado al entrar (salvo pantallas de celebración)
- [ ] Botón CTA se activa correctamente al completar el campo
- [ ] Botón ocupa `312px` de ancho (360px - 24px*2)
- [ ] Footer con `box-shadow` superior visible
- [ ] No hay colores hex hardcodeados fuera de este documento
- [ ] No hay `font-family` distinto a Maison Neue
- [ ] Las imágenes tienen `alt=""` y `aria-hidden="true"` si son decorativas
