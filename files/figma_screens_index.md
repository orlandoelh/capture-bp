# Índice de pantallas — Figma node-id
## Captura de Sueño · Plan de Negocio Yanbal

**Archivo Figma:** `rfT4CY1QrYEC8xtRTOlfb5`  
**Nombre:** Plan de Negocio

> **Importante:** Todo el flujo vive en un único archivo `index.html`. Cada pantalla es un **paso (step)** dentro del mismo wizard — se muestra u oculta con JS, nunca se navega a otra URL.

---

| # | Nombre del paso | ID del step (HTML) | Node ID Figma | Link Figma |
|---|---|---|---|---|
| 0 | Intro / Home | `step-0` | `1029-41190` | [Ver en Figma](https://www.figma.com/design/rfT4CY1QrYEC8xtRTOlfb5/Plan-de-Negocio?node-id=1029-41190&m=dev) |
| 1 | Antes de comenzar | `step-1` | `1029-36171` | [Ver en Figma](https://www.figma.com/design/rfT4CY1QrYEC8xtRTOlfb5/Plan-de-Negocio?node-id=1029-36171&m=dev) |
| 2 | Intro sueño personal | `step-2` | `1029-27842` | [Ver en Figma](https://www.figma.com/design/rfT4CY1QrYEC8xtRTOlfb5/Plan-de-Negocio?node-id=1029-27842&m=dev) |
| 3 | Sueño: texto libre | `step-3` | `1029-25328` | [Ver en Figma](https://www.figma.com/design/rfT4CY1QrYEC8xtRTOlfb5/Plan-de-Negocio?node-id=1029-25328&m=dev) |
| 4 | Sueño: imagen | `step-4` | `1029-28697` | [Ver en Figma](https://www.figma.com/design/rfT4CY1QrYEC8xtRTOlfb5/Plan-de-Negocio?node-id=1029-28697&m=dev) |
| 5 | Sueño: costo | `step-5` | `1029-23300` | [Ver en Figma](https://www.figma.com/design/rfT4CY1QrYEC8xtRTOlfb5/Plan-de-Negocio?node-id=1029-23300&m=dev) |
| 6 | Sueño: campaña meta | `step-6` | `1029-25804` | [Ver en Figma](https://www.figma.com/design/rfT4CY1QrYEC8xtRTOlfb5/Plan-de-Negocio?node-id=1029-25804&m=dev) |
| 7 | Resultado / celebración | `step-7` | `1029-36572` | [Ver en Figma](https://www.figma.com/design/rfT4CY1QrYEC8xtRTOlfb5/Plan-de-Negocio?node-id=1029-36572&m=dev) |
| 8 | Motor: texto libre | `step-8` | `1029-28675` | [Ver en Figma](https://www.figma.com/design/rfT4CY1QrYEC8xtRTOlfb5/Plan-de-Negocio?node-id=1029-28675&m=dev) |
| 9 | Motor: imagen | `step-9` | `1029-32414` | [Ver en Figma](https://www.figma.com/design/rfT4CY1QrYEC8xtRTOlfb5/Plan-de-Negocio?node-id=1029-32414&m=dev) |
| 10 | Cierre | `step-10` | `1029-27830` | [Ver en Figma](https://www.figma.com/design/rfT4CY1QrYEC8xtRTOlfb5/Plan-de-Negocio?node-id=1029-27830&m=dev) |

---

## Estructura del wizard en index.html

```html
<!-- Cada paso es un div que se muestra/oculta -->
<div id="step-0" class="step active">...</div>
<div id="step-1" class="step hidden">...</div>
<div id="step-2" class="step hidden">...</div>
<!-- ... hasta step-10 -->
```

```css
.step { display: none; }
.step.active { display: flex; }
```

```javascript
// Navegación entre pasos
let currentStep = 0;
const totalSteps = 10;

function goToStep(n) {
  document.getElementById(`step-${currentStep}`).classList.remove('active');
  document.getElementById(`step-${currentStep}`).classList.add('hidden');
  currentStep = n;
  document.getElementById(`step-${currentStep}`).classList.add('active');
  document.getElementById(`step-${currentStep}`).classList.remove('hidden');
  updateProgressBar();
}

function nextStep() { goToStep(currentStep + 1); }
function prevStep() { goToStep(currentStep - 1); }

function updateProgressBar() {
  const pct = (currentStep / totalSteps) * 100;
  document.getElementById('progress-fill').style.width = `${pct}%`;
}
```

---

## Notas

- Las pantallas 0, 1, 2, 7 y 10 son **intro/celebración** — el botón CTA arranca activo.
- Las pantallas 3, 4, 5, 6, 8 y 9 son **captura** — el botón CTA arranca deshabilitado hasta que el campo tiene valor.
- El progreso se calcula como `(step_actual / 10) * 100%`.
- El estado del formulario (sueño, costo, campaña, motor) se guarda en un objeto JS global durante la sesión.
