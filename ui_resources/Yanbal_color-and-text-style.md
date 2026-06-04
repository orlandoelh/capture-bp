# FrYDA · Design System — Librería de Color y Tipografía

> **Source of Truth** para Claude Code. Generado desde `tokens.json` (Token Studio / Figma Variables) y la página **Tipography** del archivo FrYDA en Figma.
> Fuente: **Maison Neue**. Fecha de generación: 2026-06-02.

## Convención de nomenclatura

Todas las variables siguen el prefijo `--fry-`:

| Prefijo | Capa | Significado |
|---|---|---|
| `--fry-p-*` | **Primitiva** | Valor atómico (hex, número). No usar directamente en componentes. |
| `--fry-s-*` | **Semántica** | Intención de uso. Apunta a un primitivo. **Usar esta capa en los componentes.** |

Regla de oro: **los componentes consumen tokens semánticos**, nunca primitivos ni hex literales.

---

## 1. Tipografía

### 1.1 Familia tipográfica

| Token | Valor | Variable CSS |
|---|---|---|
| `font.family.primary` | Maison Neue | `--fry-s-font-family-primary` |

### 1.2 Pesos disponibles (archivos `.otf`)

| Peso | font-weight | Archivo | Token semántico |
|---|---|---|---|
| Thin | 100 | `MaisonNeue-Thin.otf` | — |
| Light | 300 | `MaisonNeue-Light.otf` | — |
| Book | **400** | `MaisonNeue-Book.otf` | `--fry-s-font-weight-400` |
| Demi | **600** | `MaisonNeue-Demi.otf` | `--fry-s-font-weight-600` |

> El DS define formalmente solo **400 (Book)** y **600 (Demi)**. Thin y Light se incluyen para usos editoriales/marketing. Cada peso tiene su variante itálica.

### 1.3 Escalas tipográficas (tokens semánticos)

**Tamaños** (`--fry-s-font-size-*`)

| Token | px |
|---|---|
| `--fry-s-font-size-s` | 12 |
| `--fry-s-font-size-m` | 14 |
| `--fry-s-font-size-l` | 16 |
| `--fry-s-font-size-xl` | 18 |
| `--fry-s-font-size-2xl` | 20 |
| `--fry-s-font-size-3xl` | 24 |
| `--fry-s-font-size-4xl` | 28 |
| `--fry-s-font-size-5xl` | 32 |
| `--fry-s-font-size-6xl` | 40 |
| `--fry-s-font-size-7xl` | 56 |
| `--fry-s-font-size-8xl` | 64 |

**Interlineado** (`--fry-s-font-line-height-*`)

| Token | px |
|---|---|
| `--fry-s-font-line-height-s` | 16 |
| `--fry-s-font-line-height-m` | 20 |
| `--fry-s-font-line-height-l` | 24 |
| `--fry-s-font-line-height-xl` | 28 |
| `--fry-s-font-line-height-2xl` | 32 |
| `--fry-s-font-line-height-3xl` | 40 |
| `--fry-s-font-line-height-4xl` | 48 |
| `--fry-s-font-line-height-5xl` | 60 |
| `--fry-s-font-line-height-6xl` | 72 |

**Tracking** (`--fry-s-font-letter-spacing-*`)

| Token | px |
|---|---|
| `--fry-s-font-letter-spacing-s` | 0.2 |

### 1.4 Declaración `@font-face`

Coloca los `.otf` en `./fonts/` junto al CSS. Bloque listo para producción:

```css
@font-face {
  font-family: "Maison Neue";
  src: url("./fonts/MaisonNeue-Thin.otf") format("opentype");
  font-weight: 100;
  font-style: normal;
  font-display: swap;
}
@font-face {
  font-family: "Maison Neue";
  src: url("./fonts/MaisonNeue-ThinItalic.otf") format("opentype");
  font-weight: 100;
  font-style: italic;
  font-display: swap;
}
@font-face {
  font-family: "Maison Neue";
  src: url("./fonts/MaisonNeue-Light.otf") format("opentype");
  font-weight: 300;
  font-style: normal;
  font-display: swap;
}
@font-face {
  font-family: "Maison Neue";
  src: url("./fonts/MaisonNeue-LightItalic.otf") format("opentype");
  font-weight: 300;
  font-style: italic;
  font-display: swap;
}
@font-face {
  font-family: "Maison Neue";
  src: url("./fonts/MaisonNeue-Book.otf") format("opentype");
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}
@font-face {
  font-family: "Maison Neue";
  src: url("./fonts/MaisonNeue-BookItalic.otf") format("opentype");
  font-weight: 400;
  font-style: italic;
  font-display: swap;
}
@font-face {
  font-family: "Maison Neue";
  src: url("./fonts/MaisonNeue-Demi.otf") format("opentype");
  font-weight: 600;
  font-style: normal;
  font-display: swap;
}
@font-face {
  font-family: "Maison Neue";
  src: url("./fonts/MaisonNeue-DemiItalic.otf") format("opentype");
  font-weight: 600;
  font-style: italic;
  font-display: swap;
}
```

## 2. Estilos tipográficos (Text Styles)

Extraídos de la página **Tipography** de Figma. Todos usan `font-family: Maison Neue` y `letter-spacing: 0.2px`.

### 2.1 Headings

| Estilo | Tamaño (px) | Interlineado (px) | Peso |
|---|---|---|---|
| **Heading 1** | 56 | 80 | Demi (600) |
| **Heading 2** | 40 | 56 | Demi (600) |
| **Heading 3** | 32 | 40 | Demi (600) |
| **Heading 4** | 24 | 32 | Demi (600) |
| **Heading 5** | 22 | 32 | Demi (600) |
| **Heading 6** | 20 | 32 | Demi (600) |
| **Heading 7** | 18 | 24 | Demi (600) |
| **Heading 8** | 16 | 24 | Demi (600) |

### 2.2 Body / Paragraph

Cada tamaño existe en **Book (400)** y **Demi (600)**, con variantes `underline`. El interlineado sigue la regla del DS size↔line-height por sufijo.

| Estilo | Tamaño (px) | Interlineado (px) | Pesos | Notas |
|---|---|---|---|---|
| Paragraph 18 | 18 | 28 | Book / Demi | + Underline |
| Paragraph 16 | 16 | 24 | Book / Demi | + Underline |
| Paragraph 14 | 14 | 20 | Book / Demi | + Underline |
| Paragraph 12 | 12 | 16 | Book / Demi | + Underline |
| Paragraph 10 | 10 | 16 | Book / Demi | + Underline |

### 2.3 Estilos especiales (Precio)

| Estilo | Tamaño (px) | Interlineado (px) | Peso | Notas |
|---|---|---|---|---|
| **Price** | 24 | 40 | Demi (600) | Precio de venta destacado |
| **Old Price** | 24 | 32 | Book (400) | Precio anterior — aplicar `text-decoration: line-through` |

### 2.4 Ejemplo de clases CSS

```css
.fry-heading-1 {
  font-family: "Maison Neue", sans-serif;
  font-size: 56px;
  line-height: 80px;
  font-weight: 600;
  letter-spacing: 0.2px;
}
.fry-heading-4 {
  font-family: "Maison Neue", sans-serif;
  font-size: 24px;
  line-height: 32px;
  font-weight: 600;
  letter-spacing: 0.2px;
}
.fry-paragraph-16-book {
  font-family: "Maison Neue", sans-serif;
  font-size: 16px;
  line-height: 24px;
  font-weight: 400;
  letter-spacing: 0.2px;
}
.fry-paragraph-14-demi {
  font-family: "Maison Neue", sans-serif;
  font-size: 14px;
  line-height: 20px;
  font-weight: 600;
  letter-spacing: 0.2px;
}
.fry-price {
  font-family: "Maison Neue", sans-serif;
  font-size: 24px;
  line-height: 40px;
  font-weight: 600;
  letter-spacing: 0.2px;
}
```

---

## 3. Color — Capa Primitiva

`--fry-p-color-{familia}-{step}`. Cada familia tiene 10 pasos (10 = más claro → 100 = base/más oscuro).

### 3.1 Semántica de la escala (10–100)

| Step | Significado |
|---|---|
| 10 | Tono más claro. Máxima luminosidad, mínima saturación. |
| 20 | Tono suave, cercano a fondos claros. Mínima intensidad. |
| 30 | Tono muy claro. Alta luminosidad, baja presencia cromática. |
| 40 | Tono claro con reducción de saturación. Menor peso visual. |
| 50 | Tono neutro de referencia. Punto central de la escala. |
| 60 | Tono medio. Saturación equilibrada y luminosidad moderada. |
| 70 | Transición entre tonos oscuros y medios. Balance de fuerza. |
| 80 | Tono oscuro con leve incremento de luminosidad. |
| 90 | Muy cercano al tono base, ligeramente más claro. |
| 100 | Tono base. Máxima profundidad cromática, menor luminosidad. |

### 3.2 Familias

#### Yanbal Orange
_Color de marca primario Yanbal._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#fff4ef` | `--fry-p-color-yanbal-orange-10` |
| 20 | `#fde4da` | `--fry-p-color-yanbal-orange-20` |
| 30 | `#f9c7b6` | `--fry-p-color-yanbal-orange-30` |
| 40 | `#f2a284` | `--fry-p-color-yanbal-orange-40` |
| 50 | `#e67b52` | `--fry-p-color-yanbal-orange-50` |
| 60 | `#d95f34` | `--fry-p-color-yanbal-orange-60` |
| 70 | `#cf5328` | `--fry-p-color-yanbal-orange-70` |
| 80 | `#c94e22` | `--fry-p-color-yanbal-orange-80` |
| 90 | `#a83c18` | `--fry-p-color-yanbal-orange-90` |
| 100 | `#7a2e14` | `--fry-p-color-yanbal-orange-100` |

#### Coconut
_Tono para uso en entornos neutrales con un toque cálido._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#fff2e8` | `--fry-p-color-coconut-10` |
| 20 | `#feebdd` | `--fry-p-color-coconut-20` |
| 30 | `#ffdfc6` | `--fry-p-color-coconut-30` |
| 40 | `#fcd8ba` | `--fry-p-color-coconut-40` |
| 50 | `#ffcba4` | `--fry-p-color-coconut-50` |
| 60 | `#ffbe8e` | `--fry-p-color-coconut-60` |
| 70 | `#e6a97c` | `--fry-p-color-coconut-70` |
| 80 | `#cc9468` | `--fry-p-color-coconut-80` |
| 90 | `#a87650` | `--fry-p-color-coconut-90` |
| 100 | `#7a573a` | `--fry-p-color-coconut-100` |

#### Salt
_Tono terroso para uso en entornos neutrales o sin carga semántica._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#f8f1ef` | `--fry-p-color-salt-10` |
| 20 | `#f5ebe7` | `--fry-p-color-salt-20` |
| 30 | `#ebd7d0` | `--fry-p-color-salt-30` |
| 40 | `#e0c3b8` | `--fry-p-color-salt-40` |
| 50 | `#cfa99d` | `--fry-p-color-salt-50` |
| 60 | `#b88e82` | `--fry-p-color-salt-60` |
| 70 | `#9c7468` | `--fry-p-color-salt-70` |
| 80 | `#7f5a4f` | `--fry-p-color-salt-80` |
| 90 | `#5f4238` | `--fry-p-color-salt-90` |
| 100 | `#402c24` | `--fry-p-color-salt-100` |

#### Marigold
_Paleta de color de warning o advertencia._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#fff7eb` | `--fry-p-color-marigold-10` |
| 20 | `#ffe9c6` | `--fry-p-color-marigold-20` |
| 30 | `#ffcf88` | `--fry-p-color-marigold-30` |
| 40 | `#ffb049` | `--fry-p-color-marigold-40` |
| 50 | `#ffa133` | `--fry-p-color-marigold-50` |
| 60 | `#ff9420` | `--fry-p-color-marigold-60` |
| 70 | `#f96f07` | `--fry-p-color-marigold-70` |
| 80 | `#d95e06` | `--fry-p-color-marigold-80` |
| 90 | `#b24b05` | `--fry-p-color-marigold-90` |
| 100 | `#7a3303` | `--fry-p-color-marigold-100` |

#### Yanbal Black
_Neutro corporativo. Base de texto, superficies y bordes._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#ffffff` | `--fry-p-color-yanbal-black-10` |
| 20 | `#e6e8ec` | `--fry-p-color-yanbal-black-20` |
| 30 | `#c4c7ce` | `--fry-p-color-yanbal-black-30` |
| 40 | `#a1a5ae` | `--fry-p-color-yanbal-black-40` |
| 50 | `#858993` | `--fry-p-color-yanbal-black-50` |
| 60 | `#6e727c` | `--fry-p-color-yanbal-black-60` |
| 70 | `#575b66` | `--fry-p-color-yanbal-black-70` |
| 80 | `#414550` | `--fry-p-color-yanbal-black-80` |
| 90 | `#2c2f39` | `--fry-p-color-yanbal-black-90` |
| 100 | `#1c1f28` | `--fry-p-color-yanbal-black-100` |

#### Peach
_Color de marca con tono suave, se usa como apoyo cuando el Yanbal Orange es demasiado intenso para ese espacio._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#fef3ed` | `--fry-p-color-peach-10` |
| 20 | `#fde6e0` | `--fry-p-color-peach-20` |
| 30 | `#facec1` | `--fry-p-color-peach-30` |
| 40 | `#f7b7a2` | `--fry-p-color-peach-40` |
| 50 | `#f49e83` | `--fry-p-color-peach-50` |
| 60 | `#ff8a62` | `--fry-p-color-peach-60` |
| 70 | `#e67652` | `--fry-p-color-peach-70` |
| 80 | `#cc6244` | `--fry-p-color-peach-80` |
| 90 | `#a34c35` | `--fry-p-color-peach-90` |
| 100 | `#733426` | `--fry-p-color-peach-100` |

#### Bone
_Color de uso neutral, para fondos en nivel terciario._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#f8f7f4` | `--fry-p-color-bone-10` |
| 20 | `#f1efea` | `--fry-p-color-bone-20` |
| 30 | `#edece4` | `--fry-p-color-bone-30` |
| 40 | `#dfdccf` | `--fry-p-color-bone-40` |
| 50 | `#cfcbbe` | `--fry-p-color-bone-50` |
| 60 | `#b8b4a6` | `--fry-p-color-bone-60` |
| 70 | `#9e9a8c` | `--fry-p-color-bone-70` |
| 80 | `#838072` | `--fry-p-color-bone-80` |
| 90 | `#646155` | `--fry-p-color-bone-90` |
| 100 | `#4a473d` | `--fry-p-color-bone-100` |

#### Pistachio
_Tono verdoso sin carga semántica, se principalmente en los entornos comerciales._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#ecf0ed` | `--fry-p-color-pistachio-10` |
| 20 | `#c7d1c8` | `--fry-p-color-pistachio-20` |
| 30 | `#a2b2a3` | `--fry-p-color-pistachio-30` |
| 40 | `#58745a` | `--fry-p-color-pistachio-40` |
| 50 | `#4f6a51` | `--fry-p-color-pistachio-50` |
| 60 | `#465f47` | `--fry-p-color-pistachio-60` |
| 70 | `#3b523c` | `--fry-p-color-pistachio-70` |
| 80 | `#2f4230` | `--fry-p-color-pistachio-80` |
| 90 | `#243225` | `--fry-p-color-pistachio-90` |
| 100 | `#19231a` | `--fry-p-color-pistachio-100` |

#### Olive
_Tono verdoso más intenso, se usa principalmente en los entornos comerciales._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#f4f5ec` | `--fry-p-color-olive-10` |
| 20 | `#d2d6b2` | `--fry-p-color-olive-20` |
| 30 | `#bcc28b` | `--fry-p-color-olive-30` |
| 40 | `#9aa351` | `--fry-p-color-olive-40` |
| 50 | `#8c9449` | `--fry-p-color-olive-50` |
| 60 | `#7d853f` | `--fry-p-color-olive-60` |
| 70 | `#6d7436` | `--fry-p-color-olive-70` |
| 80 | `#585f2c` | `--fry-p-color-olive-80` |
| 90 | `#434823` | `--fry-p-color-olive-90` |
| 100 | `#2e3218` | `--fry-p-color-olive-100` |

#### Aegean
_Tono verdoso azulado, se usa principalmente en los entornos comerciales._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#e5eef1` | `--fry-p-color-aegean-10` |
| 20 | `#b2ccd4` | `--fry-p-color-aegean-20` |
| 30 | `#669aa9` | `--fry-p-color-aegean-30` |
| 40 | `#3f8395` | `--fry-p-color-aegean-40` |
| 50 | `#1a677e` | `--fry-p-color-aegean-50` |
| 60 | `#155467` | `--fry-p-color-aegean-60` |
| 70 | `#12495a` | `--fry-p-color-aegean-70` |
| 80 | `#0e3c4a` | `--fry-p-color-aegean-80` |
| 90 | `#0a2f3a` | `--fry-p-color-aegean-90` |
| 100 | `#061f27` | `--fry-p-color-aegean-100` |

#### Mint
_Paleta de color de éxito, success o para mostrar que algo está completado._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#e8f8f9` | `--fry-p-color-mint-10` |
| 20 | `#beebec` | `--fry-p-color-mint-20` |
| 30 | `#86d4d6` | `--fry-p-color-mint-30` |
| 40 | `#58c1c4` | `--fry-p-color-mint-40` |
| 50 | `#2eb0b4` | `--fry-p-color-mint-50` |
| 60 | `#2aa6aa` | `--fry-p-color-mint-60` |
| 70 | `#27999d` | `--fry-p-color-mint-70` |
| 80 | `#1f8084` | `--fry-p-color-mint-80` |
| 90 | `#16666a` | `--fry-p-color-mint-90` |
| 100 | `#0e4c4f` | `--fry-p-color-mint-100` |

#### Crimson
_Paleta de color de error, peligro o danger._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#fce5e4` | `--fry-p-color-crimson-10` |
| 20 | `#fbcfcd` | `--fry-p-color-crimson-20` |
| 30 | `#f7adaa` | `--fry-p-color-crimson-30` |
| 40 | `#f07e79` | `--fry-p-color-crimson-40` |
| 50 | `#e5554f` | `--fry-p-color-crimson-50` |
| 60 | `#b02b25` | `--fry-p-color-crimson-60` |
| 70 | `#792623` | `--fry-p-color-crimson-70` |
| 80 | `#5f1d1a` | `--fry-p-color-crimson-80` |
| 90 | `#471514` | `--fry-p-color-crimson-90` |
| 100 | `#300e0d` | `--fry-p-color-crimson-100` |

#### Slate
_Tono azulado más neutral, se usa principalmente en los entornos comerciales.._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#f4f6f6` | `--fry-p-color-slate-10` |
| 20 | `#e8eced` | `--fry-p-color-slate-20` |
| 30 | `#c6d0d2` | `--fry-p-color-slate-30` |
| 40 | `#99aaae` | `--fry-p-color-slate-40` |
| 50 | `#7f9398` | `--fry-p-color-slate-50` |
| 60 | `#667c82` | `--fry-p-color-slate-60` |
| 70 | `#4f666c` | `--fry-p-color-slate-70` |
| 80 | `#3a4f54` | `--fry-p-color-slate-80` |
| 90 | `#27383c` | `--fry-p-color-slate-90` |
| 100 | `#182629` | `--fry-p-color-slate-100` |

#### Wine
_Paleta de color comercial, se usa principalmente cuando una perfil no se encuentra incorporado a Yanbal y tiene la capacidad de de re-incorporado._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#f9f0f5` | `--fry-p-color-wine-10` |
| 20 | `#e8d4df` | `--fry-p-color-wine-20` |
| 30 | `#c7b5bf` | `--fry-p-color-wine-30` |
| 40 | `#a07a8d` | `--fry-p-color-wine-40` |
| 50 | `#81586f` | `--fry-p-color-wine-50` |
| 60 | `#734c62` | `--fry-p-color-wine-60` |
| 70 | `#653f55` | `--fry-p-color-wine-70` |
| 80 | `#573348` | `--fry-p-color-wine-80` |
| 90 | `#47293a` | `--fry-p-color-wine-90` |
| 100 | `#361e2b` | `--fry-p-color-wine-100` |

#### Blue
_Paleta de color informativa, se usa además en los perfil recientemente incorproados a Yanbal._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#f0f7ff` | `--fry-p-color-blue-10` |
| 20 | `#e0eefe` | `--fry-p-color-blue-20` |
| 30 | `#b9ddfe` | `--fry-p-color-blue-30` |
| 40 | `#7cc3fd` | `--fry-p-color-blue-40` |
| 50 | `#36a5fa` | `--fry-p-color-blue-50` |
| 60 | `#0066bf` | `--fry-p-color-blue-60` |
| 70 | `#0155a3` | `--fry-p-color-blue-70` |
| 80 | `#0b3d6f` | `--fry-p-color-blue-80` |
| 90 | `#082e54` | `--fry-p-color-blue-90` |
| 100 | `#051f3a` | `--fry-p-color-blue-100` |

#### Magenta
_Tono magenta, se usa principalmente en los entornos comerciales.._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#ffd6ec` | `--fry-p-color-magenta-10` |
| 20 | `#f7a3cf` | `--fry-p-color-magenta-20` |
| 30 | `#f36bb4` | `--fry-p-color-magenta-30` |
| 40 | `#e00077` | `--fry-p-color-magenta-40` |
| 50 | `#b0005f` | `--fry-p-color-magenta-50` |
| 60 | `#8f004c` | `--fry-p-color-magenta-60` |
| 70 | `#74003e` | `--fry-p-color-magenta-70` |
| 80 | `#5a0031` | `--fry-p-color-magenta-80` |
| 90 | `#430024` | `--fry-p-color-magenta-90` |
| 100 | `#2d0018` | `--fry-p-color-magenta-100` |

#### Purple
_Tono purpura inteso, se usa principalmente en los entornos comerciales.._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#f3e6f4` | `--fry-p-color-purple-10` |
| 20 | `#d9b6db` | `--fry-p-color-purple-20` |
| 30 | `#b97fbc` | `--fry-p-color-purple-30` |
| 40 | `#9c4fa2` | `--fry-p-color-purple-40` |
| 50 | `#820085` | `--fry-p-color-purple-50` |
| 60 | `#6e0073` | `--fry-p-color-purple-60` |
| 70 | `#5a0060` | `--fry-p-color-purple-70` |
| 80 | `#48004d` | `--fry-p-color-purple-80` |
| 90 | `#37003b` | `--fry-p-color-purple-90` |
| 100 | `#28002b` | `--fry-p-color-purple-100` |

#### Pink
_Tono rosado claro, se usa principalmente en los entornos comerciales._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#fce5f1` | `--fry-p-color-pink-10` |
| 20 | `#f8e5f8` | `--fry-p-color-pink-20` |
| 30 | `#f3c9e2` | `--fry-p-color-pink-30` |
| 40 | `#efaad0` | `--fry-p-color-pink-40` |
| 50 | `#e887bc` | `--fry-p-color-pink-50` |
| 60 | `#d96aa7` | `--fry-p-color-pink-60` |
| 70 | `#bf4f8e` | `--fry-p-color-pink-70` |
| 80 | `#9e3c73` | `--fry-p-color-pink-80` |
| 90 | `#7a2c59` | `--fry-p-color-pink-90` |
| 100 | `#561d40` | `--fry-p-color-pink-100` |

#### Green
_Tono verde intenso, se usa principalmente en los entornos comerciales.._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#e6f7ea` | `--fry-p-color-green-10` |
| 20 | `#c2efcb` | `--fry-p-color-green-20` |
| 30 | `#8fe3a1` | `--fry-p-color-green-30` |
| 40 | `#4fd66f` | `--fry-p-color-green-40` |
| 50 | `#1fcb3f` | `--fry-p-color-green-50` |
| 60 | `#00bf16` | `--fry-p-color-green-60` |
| 70 | `#00a514` | `--fry-p-color-green-70` |
| 80 | `#005c0b` | `--fry-p-color-green-80` |
| 90 | `#004809` | `--fry-p-color-green-90` |
| 100 | `#003306` | `--fry-p-color-green-100` |

#### Indigo
_Tono indigo intenso, se usa principalmente en los entornos comerciales.._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#e5e7f8` | `--fry-p-color-indigo-10` |
| 20 | `#c7cbf2` | `--fry-p-color-indigo-20` |
| 30 | `#a5abe9` | `--fry-p-color-indigo-30` |
| 40 | `#8086df` | `--fry-p-color-indigo-40` |
| 50 | `#6c72d1` | `--fry-p-color-indigo-50` |
| 60 | `#575fc2` | `--fry-p-color-indigo-60` |
| 70 | `#444cb0` | `--fry-p-color-indigo-70` |
| 80 | `#383f96` | `--fry-p-color-indigo-80` |
| 90 | `#2c327a` | `--fry-p-color-indigo-90` |
| 100 | `#21265f` | `--fry-p-color-indigo-100` |

#### Pearl
_Paleta de color de soporte para superficies neutrales que necesitan un tono cálido, se usa al igual que Bone en una 2da o 3ra jerarquía._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#f8f7f4` | `--fry-p-color-pearl-10` |
| 20 | `#f5f3ef` | `--fry-p-color-pearl-20` |
| 30 | `#f1efea` | `--fry-p-color-pearl-30` |
| 40 | `#eae8df` | `--fry-p-color-pearl-40` |
| 50 | `#e3e0d5` | `--fry-p-color-pearl-50` |
| 60 | `#dfdccf` | `--fry-p-color-pearl-60` |
| 70 | `#c9c6ba` | `--fry-p-color-pearl-70` |
| 80 | `#b2afa3` | `--fry-p-color-pearl-80` |
| 90 | `#8f8c81` | `--fry-p-color-pearl-90` |
| 100 | `#6c6a60` | `--fry-p-color-pearl-100` |

#### Yanbal Black Overlay
_Variante con canal alfa del negro de marca (overlays)._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#1c1f281a` | `--fry-p-color-yanbal-black-overlay-10` |
| 20 | `#1c1f2833` | `--fry-p-color-yanbal-black-overlay-20` |
| 30 | `#1c1f284d` | `--fry-p-color-yanbal-black-overlay-30` |
| 40 | `#1c1f2866` | `--fry-p-color-yanbal-black-overlay-40` |
| 50 | `#1c1f2880` | `--fry-p-color-yanbal-black-overlay-50` |
| 60 | `#1c1f2899` | `--fry-p-color-yanbal-black-overlay-60` |
| 70 | `#1c1f28b3` | `--fry-p-color-yanbal-black-overlay-70` |
| 80 | `#1c1f28cc` | `--fry-p-color-yanbal-black-overlay-80` |
| 90 | `#1c1f28e6` | `--fry-p-color-yanbal-black-overlay-90` |
| 100 | `#1c1f28fc` | `--fry-p-color-yanbal-black-overlay-100` |

#### Yanbal Orange Overlay
_Variante con canal alfa del naranja de marca (overlays)._

| Step | Hex | Variable CSS |
|---|---|---|
| 10 | `#c94e221a` | `--fry-p-color-yanbal-orange-overlay-10` |
| 20 | `#c94e2233` | `--fry-p-color-yanbal-orange-overlay-20` |
| 30 | `#c94e224d` | `--fry-p-color-yanbal-orange-overlay-30` |
| 40 | `#c94e2266` | `--fry-p-color-yanbal-orange-overlay-40` |
| 50 | `#c94e2280` | `--fry-p-color-yanbal-orange-overlay-50` |
| 60 | `#c94e2299` | `--fry-p-color-yanbal-orange-overlay-60` |
| 70 | `#c94e22b3` | `--fry-p-color-yanbal-orange-overlay-70` |
| 80 | `#c94e22cc` | `--fry-p-color-yanbal-orange-overlay-80` |
| 90 | `#c94e22e6` | `--fry-p-color-yanbal-orange-overlay-90` |
| 100 | `#c94e22fc` | `--fry-p-color-yanbal-orange-overlay-100` |

---

## 4. Color — Capa Semántica (Light)

Tokens de intención. **Esta es la capa que consumen los componentes.** Cada token apunta a un primitivo (resuelto a hex abajo).

### 4.1 Content (texto e iconos)

| Token | Hex | Apunta a | Variable CSS | Descripción |
|---|---|---|---|---|
| `content.neutral.strong` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-content-neutral-strong` | Texto principal, máximo contraste. Headlines y body crítico. |
| `content.neutral.subtle` | `#858993` | `--fry-p-color-yanbal-black-50` | `--fry-s-color-content-neutral-subtle` | Texto secundario, metadatos, captions. |
| `content.neutral.inverse` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-content-neutral-inverse` | Texto sobre fondos oscuros (Surface inverse). |
| `content.neutral.disabled` | `#a1a5ae` | `--fry-p-color-yanbal-black-40` | `--fry-s-color-content-neutral-disabled` | Texto en estado deshabilitado. |
| `content.neutral.base` | `#575b66` | `--fry-p-color-yanbal-black-70` | `--fry-s-color-content-neutral-base` | Texto estándar de párrafo y descripciones. |
| `content.neutral.soft` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-content-neutral-soft` | Texto terciario, placeholders. |
| `content.neutral.disabled-soft` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-content-neutral-disabled` | Texto en estado deshabilitado. |
| `content.action.primary.default` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-content-action-primary-default` | Texto/icono dentro del Call to Action primario. |
| `content.action.primary.hover` | `#fde4da` | `--fry-p-color-yanbal-orange-20` | `--fry-s-color-content-action-primary-hover` | Estado de interacción hover |
| `content.action.primary.pressed` | `#f9c7b6` | `--fry-p-color-yanbal-orange-30` | `--fry-s-color-content-action-primary-pressed` | Estados de interacción pressed |
| `content.action.primary.inverse` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-content-action-primary-inverse` | Texto/icono de Call to action. Sobre Surface inverse |
| `content.action.primary.inverse-hover` | `#414550` | `--fry-p-color-yanbal-black-80` | `--fry-s-color-content-action-primary-inverse-hover` | Estados de interacción hover. Sobre Surface inverse |
| `content.action.primary.inverse-pressed` | `#6e727c` | `--fry-p-color-yanbal-black-60` | `--fry-s-color-content-action-primary-inverse-pressed` | Estados de interacción pressed. Sobre Surface inverse |
| `content.action.secondary.default` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-content-action-secondary-default` | Texto/icono de acción secundario |
| `content.action.secondary.hover` | `#414550` | `--fry-p-color-yanbal-black-80` | `--fry-s-color-content-action-secondary-hover` | Estado de interacción hover |
| `content.action.secondary.pressed` | `#6e727c` | `--fry-p-color-yanbal-black-60` | `--fry-s-color-content-action-secondary-pressed` | Estados de interacción pressed |
| `content.action.secondary.inverse` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-content-action-secondary-inverse` | Texto/icono de acción secundario. Sobre Surface inverse |
| `content.action.secondary.inverse-hover` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-content-action-secondary-inverse-hover` | Estados de interacción hover. Sobre Surface inverse |
| `content.action.secondary.inverse-pressed` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-content-action-secondary-inverse-pressed` | Estados de interacción pressed. Sobre Surface inverse |
| `content.action.ghost.default` | `#c94e22` | `--fry-p-color-yanbal-orange-80` | `--fry-s-color-content-action-ghost-default` | Texto/icono del botón fantasma (sin fondo). |
| `content.action.ghost.hover` | `#a83c18` | `--fry-p-color-yanbal-orange-90` | `--fry-s-color-content-action-ghost-hover` | Estado de interacción hover |
| `content.action.ghost.pressed` | `#7a2e14` | `--fry-p-color-yanbal-orange-100` | `--fry-s-color-content-action-ghost-pressed` | Estados de interacción pressed |
| `content.action.ghost.inverse` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-content-action-ghost-inverse` | Texto/icono del botón fantasma (sin fondo). Para surface inverse |
| `content.action.ghost.inverse-hover` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-content-action-ghost-inverse-hover` | Estados de interacción hover. Sobre Surface inverse |
| `content.action.ghost.inverse-pressed` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-content-action-ghost-inverse-pressed` | Estados de interacción pressed. Sobre Surface inverse |
| `content.action.link.default` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-content-action-link-default` | Color de hipervínculos textuales. |
| `content.action.link.hover` | `#575b66` | `--fry-p-color-yanbal-black-70` | `--fry-s-color-content-action-link-hover` | Estado de interacción hover |
| `content.action.link.pressed` | `#a1a5ae` | `--fry-p-color-yanbal-black-40` | `--fry-s-color-content-action-link-pressed` | Estados de interacción pressed |
| `content.action.link.inverse` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-content-action-link-inverse` | Color de hipervínculos textuales. Sobre surface inverse |
| `content.action.link.inverse-hover` | `#a1a5ae` | `--fry-p-color-yanbal-black-40` | `--fry-s-color-content-action-link-inverse-hover` | Estados de interacción hover. Sobre Surface inverse |
| `content.action.link.inverse-pressed` | `#575b66` | `--fry-p-color-yanbal-black-70` | `--fry-s-color-content-action-link-inverse-pressed` | Estados de interacción pressed. Sobre Surface inverse |
| `content.action.destructive.default` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-content-action-destructive-default` | Texto de acciones irreversibles o permanentemente destructivas |
| `content.action.destructive.hover` | `#fce5e4` | `--fry-p-color-crimson-10` | `--fry-s-color-content-action-destructive-hover` | Estado de interacción hover |
| `content.action.destructive.pressed` | `#fbcfcd` | `--fry-p-color-crimson-20` | `--fry-s-color-content-action-destructive-pressed` | Estados de interacción pressed |
| `content.feedback.info.strong` | `#051f3a` | `--fry-p-color-blue-100` | `--fry-s-color-content-feedback-info-strong` | Tono oscuro de texto/icono informativo. |
| `content.feedback.info.base` | `#0155a3` | `--fry-p-color-blue-70` | `--fry-s-color-content-feedback-info-base` | Tono básico de texto/icono informativo. |
| `content.feedback.info.soft` | `#b9ddfe` | `--fry-p-color-blue-30` | `--fry-s-color-content-feedback-info-soft` | Tono claro de texto/icono informativo. |
| `content.feedback.info.subtle` | `#36a5fa` | `--fry-p-color-blue-50` | `--fry-s-color-content-feedback-info-base` | Tono básico de texto/icono informativo. |
| `content.feedback.success.strong` | `#0e4c4f` | `--fry-p-color-mint-100` | `--fry-s-color-content-feedback-success-strong` | Tono oscuro de texto/icono confirmación o éxito. |
| `content.feedback.success.base` | `#1f8084` | `--fry-p-color-mint-80` | `--fry-s-color-content-feedback-success-base` | Tono básico de texto/icono confirmación o éxito. |
| `content.feedback.success.soft` | `#86d4d6` | `--fry-p-color-mint-30` | `--fry-s-color-content-feedback-success-soft` | Tono claro de texto/icono confirmación o éxito. |
| `content.feedback.success.subtle` | `#2aa6aa` | `--fry-p-color-mint-60` | `--fry-s-color-content-feedback-success-base` | Tono básico de texto/icono confirmación o éxito. |
| `content.feedback.warning.strong` | `#7a3303` | `--fry-p-color-marigold-100` | `--fry-s-color-content-feedback-warning-strong` | Tono oscuro de texto/icono de advertencia o alerta. |
| `content.feedback.warning.base` | `#f96f07` | `--fry-p-color-marigold-70` | `--fry-s-color-content-feedback-warning-base` | Tono básico de texto/icono de advertencia o alerta. |
| `content.feedback.warning.soft` | `#ffb049` | `--fry-p-color-marigold-40` | `--fry-s-color-content-feedback-warning-soft` | Tono claro de texto/icono de advertencia o alerta. |
| `content.feedback.warning.subtle` | `#ffa133` | `--fry-p-color-marigold-50` | `--fry-s-color-content-feedback-warning-base` | Tono básico de texto/icono de advertencia o alerta. |
| `content.feedback.danger.strong` | `#300e0d` | `--fry-p-color-crimson-100` | `--fry-s-color-content-feedback-danger-strong` | Tono oscuro de texto/icono de error o peligro. |
| `content.feedback.danger.base` | `#b02b25` | `--fry-p-color-crimson-60` | `--fry-s-color-content-feedback-danger-base` | Tono básico de texto/icono de error o peligro. |
| `content.feedback.danger.soft` | `#f07e79` | `--fry-p-color-crimson-40` | `--fry-s-color-content-feedback-danger-soft` | Tono claro de texto/icono de error o peligro. |
| `content.feedback.danger.subtle` | `#e5554f` | `--fry-p-color-crimson-50` | `--fry-s-color-content-feedback-danger-base` | Tono básico de texto/icono de error o peligro. |
| `content.feedback.neutral.strong` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-content-feedback-neutral-strong` | Tono de texto/icono de feedback neutral o sin carga semántica. |
| `content.status.default.solid` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-content-status-default-solid` | Tono claro. Estado por defecto o sin clasificar. |
| `content.status.default.soft` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-content-status-default-soft` | Tono oscuro. Estado por defecto o sin clasificar. |
| `content.status.default.subtle` | `#858993` | `--fry-p-color-yanbal-black-50` | `--fry-s-color-content-status-default-solid` | Tono claro. Estado por defecto o sin clasificar. |
| `content.status.completed.solid` | `#e8f8f9` | `--fry-p-color-mint-10` | `--fry-s-color-content-status-completed-solid` | Tono claro. Estado completado o activo. |
| `content.status.completed.soft` | `#1f8084` | `--fry-p-color-mint-80` | `--fry-s-color-content-status-completed-soft` | Tono oscuro. Estado completado o activo. |
| `content.status.completed.subtle` | `#58c1c4` | `--fry-p-color-mint-40` | `--fry-s-color-content-status-completed-solid` | Tono claro. Estado completado o activo. |
| `content.status.risk.solid` | `#fff7eb` | `--fry-p-color-marigold-10` | `--fry-s-color-content-status-risk-solid` | Tono claro. Estado en riesgo, en revisión o inactivo. |
| `content.status.risk.soft` | `#b24b05` | `--fry-p-color-marigold-90` | `--fry-s-color-content-status-risk-soft` | Tono oscuro. Estado en riesgo, en revisión o inactivo. |
| `content.status.risk.subtle` | `#ffa133` | `--fry-p-color-marigold-50` | `--fry-s-color-content-status-risk-solid` | Tono claro. Estado en riesgo, en revisión o inactivo. |
| `content.status.blocked.solid` | `#fce5e4` | `--fry-p-color-crimson-10` | `--fry-s-color-content-status-blocked-solid` | Tono claro. Estado en bloqueado o con deuda. |
| `content.status.blocked.soft` | `#792623` | `--fry-p-color-crimson-70` | `--fry-s-color-content-status-blocked-soft` | Tono oscuro. Estado en bloqueado o con deuda. |
| `content.status.blocked.subtle` | `#f07e79` | `--fry-p-color-crimson-40` | `--fry-s-color-content-status-blocked-solid` | Tono claro. Estado en bloqueado o con deuda. |
| `content.status.new.solid` | `#f0f7ff` | `--fry-p-color-blue-10` | `--fry-s-color-content-status-new-solid` | Tono claro. Estado nuevo o recién ingresado. |
| `content.status.new.soft` | `#0b3d6f` | `--fry-p-color-blue-80` | `--fry-s-color-content-status-new-soft` | Tono oscuro. Estado nuevo o recién ingresado. |
| `content.status.new.subtle` | `#7cc3fd` | `--fry-p-color-blue-40` | `--fry-s-color-content-status-new-solid` | Tono claro. Estado nuevo o recién ingresado. |
| `content.status.reenroll.solid` | `#f9f0f5` | `--fry-p-color-wine-10` | `--fry-s-color-content-status-reenroll-solid` | Tono claro. Estado reingresado o reenrolado a Yanbal |
| `content.status.reenroll.soft` | `#734c62` | `--fry-p-color-wine-60` | `--fry-s-color-content-status-reenroll-soft` | Tono oscuro. Estado reingresado o reenrolado a Yanbal |
| `content.status.reenroll.subtle` | `#a07a8d` | `--fry-p-color-wine-40` | `--fry-s-color-content-status-reenroll-solid` | Tono claro. Estado reingresado o reenrolado a Yanbal |
| `content.messaging.base` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-content-messaging-base` | Texto sobre banner/módulo de comunicación. |
| `content.messaging.inverse` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-content-messaging-inverse` | Versión sobre messaging surface inverse. |
| `content.state.selected.default` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-content-state-selected-default` | Glifo/icono de control seleccionado. |
| `content.state.selected.hover` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-content-state-selected-hover` | Interacción de hover para el glifo/icono de control seleccionado. |
| `content.state.selected.pressed` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-content-state-selected-pressed` | Interacción de pressed para el glifo/icono de control seleccionado. |
| `content.state.unselected.default` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-content-state-unselected-default` | Glifo/icono de control no seleccionado. |
| `content.state.unselected.hover` | `#2c2f39` | `--fry-p-color-yanbal-black-90` | `--fry-s-color-content-state-unselected-hover` | Interacción de hover para el glifo/icono de control no seleccionado. |
| `content.state.unselected.pressed` | `#414550` | `--fry-p-color-yanbal-black-80` | `--fry-s-color-content-state-unselected-pressed` | Interacción de pressed para el glifo/icono de control no seleccionado. |
| `content.state.inactive.default` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-content-state-inactive-default` | Glifo/icono de control disponible pero no activo. |
| `content.state.inactive.hover` | `#2c2f39` | `--fry-p-color-yanbal-black-90` | `--fry-s-color-content-state-inactive-hover` | Interacción de hover para el glifo/icono de control disponible pero no activo. |
| `content.state.inactive.pressed` | `#414550` | `--fry-p-color-yanbal-black-80` | `--fry-s-color-content-state-inactive-pressed` | Interacción de pressed para el glifo/icono de control disponible pero no activo. |
| `content.state.active.default` | `#c94e22` | `--fry-p-color-yanbal-orange-80` | `--fry-s-color-content-state-active-default` | Glifo/icono de control activo/energizado |
| `content.state.active.hover` | `#a83c18` | `--fry-p-color-yanbal-orange-90` | `--fry-s-color-content-state-active-hover` | Interacción de hover para el glifo/icono de control activo/energizado |
| `content.state.active.pressed` | `#7a2e14` | `--fry-p-color-yanbal-orange-100` | `--fry-s-color-content-state-active-pressed` | Interacción de pressed para el glifo/icono de control activo/energizado |
| `content.interaction.empty.default` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-content-interaction-empty-default` | Tono base de texto/icono en estados vacíos interactivos. |
| `content.interaction.empty.hover` | `#414550` | `--fry-p-color-yanbal-black-80` | `--fry-s-color-content-interaction-empty-hover` | Interacción de hover para  texto/icono en estados vacíos interactivos. |
| `content.interaction.empty.pressed` | `#6e727c` | `--fry-p-color-yanbal-black-60` | `--fry-s-color-content-interaction-empty-pressed` | Interacción de pressed para  texto/icono en estados vacíos interactivos. |
| `content.interaction.empty.subtle` | `#858993` | `--fry-p-color-yanbal-black-50` | `--fry-s-color-content-interaction-empty-subtle` | Tono un poco claro de texto/icono en estados vacíos interactivos. |
| `content.interaction.filled.default` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-content-interaction-filled-default` | Tono base de texto/icono en estados interactivos llenados. |
| `content.interaction.filled.hover` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-content-interaction-filled-hover` | Interacción de hover para texto/icono en estados interactivos llenados |
| `content.interaction.filled.pressed` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-content-interaction-filled-pressed` | Interacción de pressed para texto/icono en estados interactivos llenados |

### 4.2 Surface (fondos)

| Token | Hex | Apunta a | Variable CSS | Descripción |
|---|---|---|---|---|
| `surface.neutral.strong` | `#575b66` | `--fry-p-color-yanbal-black-70` | `--fry-s-color-surface-neutral-strong` | Container neutro de alta prominencia. |
| `surface.neutral.soft` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-surface-neutral-soft` | Container de 2da jerarquía neutral |
| `surface.neutral.disabled` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-surface-neutral-disabled` | Container deshabilitado |
| `surface.neutral.base` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-surface-neutral-base` | Fondo principal de la página |
| `surface.neutral.inverse` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-surface-neutral-inverse` | Container oscuro/inverso |
| `surface.neutral.skeleton-start` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-surface-neutral-skeleton-start` | Extremos del gradiente skeleton (loading). |
| `surface.neutral.skeleton-end` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-surface-neutral-skeleton-end` | Extremos del gradiente skeleton (loading). |
| `surface.neutral.subtle` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-surface-neutral-subtle` | Container de 1ra jerarquía neutral |
| `surface.action.primary.default` | `#c94e22` | `--fry-p-color-yanbal-orange-80` | `--fry-s-color-surface-action-primary-default` | Fondo del Call to action primario (Color de marca) |
| `surface.action.primary.hover` | `#a83c18` | `--fry-p-color-yanbal-orange-90` | `--fry-s-color-surface-action-primary-hover` | Interacción de hover para el fondo del Call to action primario (Color de marca) |
| `surface.action.primary.pressed` | `#7a2e14` | `--fry-p-color-yanbal-orange-100` | `--fry-s-color-surface-action-primary-pressed` | Interacción de pressed para el fondo del Call to action primario (Color de marca) |
| `surface.action.primary.inverse` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-surface-action-primary-inverse` | Fondo del Call to action primario sobre fondo oscuro |
| `surface.action.primary.inverse-hover` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-surface-action-primary-inverse-hover` | Interacción de hover para el fondo del Call to action primario sobre fondo oscuro |
| `surface.action.primary.inverse-pressed` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-surface-action-primary-inverse-pressed` | Interacción de pressed para el fondo del Call to action primario sobre fondo oscuro |
| `surface.action.secondary.default` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-surface-action-secondary-default` | Fondo de la acción secundario (outline) |
| `surface.action.secondary.hover` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-surface-action-secondary-hover` | Interacción de hover para el fondo de la acción secundario (outline) |
| `surface.action.secondary.pressed` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-surface-action-secondary-pressed` | Interacción de pressed para el fondo de la acción secundario (outline) |
| `surface.action.secondary.inverse` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-surface-action-secondary-inverse` | Fondo de la acción secundario para fondo oscuro.(outline) |
| `surface.action.secondary.inverse-hover` | `#414550` | `--fry-p-color-yanbal-black-80` | `--fry-s-color-surface-action-secondary-inverse-hover` | Interacción de hover para el fondo de la acción secundario para fondo oscuro.(outline) |
| `surface.action.secondary.inverse-pressed` | `#6e727c` | `--fry-p-color-yanbal-black-60` | `--fry-s-color-surface-action-secondary-inverse-pressed` | Interacción de hover para el fondo de la acción secundario para fondo oscuro.(outline) |
| `surface.action.destructive.default` | `#b02b25` | `--fry-p-color-crimson-60` | `--fry-s-color-surface-action-destructive-default` | Fondo de acción destructiva e irreversible |
| `surface.action.destructive.hover` | `#792623` | `--fry-p-color-crimson-70` | `--fry-s-color-surface-action-destructive-hover` | Interacción de hover para el fondo de acción destructiva e irreversible |
| `surface.action.destructive.pressed` | `#5f1d1a` | `--fry-p-color-crimson-80` | `--fry-s-color-surface-action-destructive-pressed` | Interacción de pressed para el fondo de acción destructiva e irreversible |
| `surface.action.ghost.default` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-surface-action-ghost-default` | Fondo de acción fantasma |
| `surface.action.ghost.hover` | `#fff4ef` | `--fry-p-color-yanbal-orange-10` | `--fry-s-color-surface-action-ghost-hover` | Interacción de hover para el fondo de acción fantasma |
| `surface.action.ghost.pressed` | `#fde4da` | `--fry-p-color-yanbal-orange-20` | `--fry-s-color-surface-action-ghost-pressed` | Interacción de pressed para el fondo de acción fantasma |
| `surface.action.ghost.inverse` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-surface-action-ghost-inverse` | Fondo de acción fantasma para superficia oscura |
| `surface.action.ghost.inverse-hover` | `#414550` | `--fry-p-color-yanbal-black-80` | `--fry-s-color-surface-action-ghost-inverse-hover` | Interacción de hover para el fondo de acción fantasma para superficia oscura |
| `surface.action.ghost.inverse-pressed` | `#6e727c` | `--fry-p-color-yanbal-black-60` | `--fry-s-color-surface-action-ghost-inverse-pressed` | Interacción de pressed para el fondo de acción fantasma para superficia oscura |
| `surface.action.tertiary.default` | `#f5f3ef` | `--fry-p-color-pearl-20` | `--fry-s-color-surface-action-tertiary-default` | Fondo de acción terciario |
| `surface.action.tertiary.hover` | `#e3e0d5` | `--fry-p-color-pearl-50` | `--fry-s-color-surface-action-tertiary-hover` | Interacción de hover para el fondo de acción terciario |
| `surface.action.tertiary.pressed` | `#dfdccf` | `--fry-p-color-pearl-60` | `--fry-s-color-surface-action-tertiary-pressed` | Interacción de pressed para el fondo de acción terciario |
| `surface.feedback.info.base` | `#f0f7ff` | `--fry-p-color-blue-10` | `--fry-s-color-surface-feedback-info-base` | Fondo de mensaje informativo. |
| `surface.feedback.success.base` | `#e8f8f9` | `--fry-p-color-mint-10` | `--fry-s-color-surface-feedback-success-base` | Fondo de confirmación. |
| `surface.feedback.warning.base` | `#fff7eb` | `--fry-p-color-marigold-10` | `--fry-s-color-surface-feedback-warning-base` | Fondo de advertencia. |
| `surface.feedback.danger.base` | `#fce5e4` | `--fry-p-color-crimson-10` | `--fry-s-color-surface-feedback-danger-base` | Fondo de error. |
| `surface.feedback.neutral.base` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-surface-feedback-neutral-base` | Fondo de feedback sin carga semántica. |
| `surface.overlay.neutral.10%` | `#1c1f281a` | `--fry-p-color-yanbal-black-overlay-10` | `--fry-s-color-surface-overlay-neutral-10%` | Capa traslúcida de Yanbal Black al 10%, Se usa para backdrops o superficies que deben ser traslúcidas |
| `surface.overlay.neutral.20%` | `#1c1f2833` | `--fry-p-color-yanbal-black-overlay-20` | `--fry-s-color-surface-overlay-neutral-20%` | Capa traslúcida de Yanbal Black al 20%, Se usa para backdrops o superficies que deben ser traslúcidas |
| `surface.overlay.neutral.80%` | `#1c1f28cc` | `--fry-p-color-yanbal-black-overlay-80` | `--fry-s-color-surface-overlay-neutral-80%` | Capa traslúcida de Yanbal Black al 80%, Se usa para backdrops o superficies que deben ser traslúcidas |
| `surface.overlay.neutral.40%` | `#1c1f2866` | `--fry-p-color-yanbal-black-overlay-40` | `--fry-s-color-surface-overlay-neutral-40%` | Capa traslúcida de Yanbal Black al 40%, Se usa para backdrops o superficies que deben ser traslúcidas |
| `surface.overlay.action.10%` | `#c94e221a` | `--fry-p-color-yanbal-orange-overlay-10` | `--fry-s-color-surface-overlay-action-10%` | Capa traslúcida con tinte Yanbal-orange al 10% |
| `surface.overlay.action.20%` | `#c94e2233` | `--fry-p-color-yanbal-orange-overlay-20` | `--fry-s-color-surface-overlay-action-20%` | Capa traslúcida con tinte Yanbal-orange al 20% |
| `surface.status.default.solid` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-surface-status-default-solid` | Uso en badges y tag sin clasificar |
| `surface.status.default.soft` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-surface-status-default-soft` | Uso en badges y tag sin clasificar |
| `surface.status.completed.solid` | `#1f8084` | `--fry-p-color-mint-80` | `--fry-s-color-surface-status-completed-solid` | Uso en badges y tag con estatus activos, online o completo. |
| `surface.status.completed.soft` | `#e8f8f9` | `--fry-p-color-mint-10` | `--fry-s-color-surface-status-completed-soft` | Uso en badges y tag con estatus activos, online o completo. |
| `surface.status.risk.solid` | `#b24b05` | `--fry-p-color-marigold-90` | `--fry-s-color-surface-status-risk-solid` | Uso en badges y tag con estatus inactivos, en riegos o incompletos. |
| `surface.status.risk.soft` | `#fff7eb` | `--fry-p-color-marigold-10` | `--fry-s-color-surface-status-risk-soft` | Uso en badges y tag con estatus inactivos, en riegos o incompletos. |
| `surface.status.blocked.solid` | `#b02b25` | `--fry-p-color-crimson-60` | `--fry-s-color-surface-status-blocked-solid` | Uso en badges y tag con estatus con deuda o bloqueado. |
| `surface.status.blocked.soft` | `#fce5e4` | `--fry-p-color-crimson-10` | `--fry-s-color-surface-status-blocked-soft` | Uso en badges y tag con estatus con deuda o bloqueado. |
| `surface.status.new.solid` | `#0066bf` | `--fry-p-color-blue-60` | `--fry-s-color-surface-status-new-solid` | Uso en badges y tag con estatus nuevo o recien incorporado o reciente. |
| `surface.status.new.soft` | `#f0f7ff` | `--fry-p-color-blue-10` | `--fry-s-color-surface-status-new-soft` | Uso en badges y tag con estatus nuevo o recien incorporado o reciente. |
| `surface.status.reenroll.solid` | `#734c62` | `--fry-p-color-wine-60` | `--fry-s-color-surface-status-reenroll-solid` | Uso en badges y tag con estatus de potencial reincorporación |
| `surface.status.reenroll.soft` | `#f9f0f5` | `--fry-p-color-wine-10` | `--fry-s-color-surface-status-reenroll-soft` | Uso en badges y tag con estatus de potencial reincorporación |
| `surface.messaging.base` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-surface-messaging-base` | Fondo de banner/módulo comunicacional. |
| `surface.messaging.inverse` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-surface-messaging-inverse` | Versión clara sobre fondo oscuro. |
| `surface.system.scrollbar.track` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-surface-system-scrollbar-track` | Track de scrollbars custom. |
| `surface.system.scrollbar.thumb` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-surface-system-scrollbar-thumb` | Thumb de scrollbars custom. |
| `surface.system.loading` | `#f8f7f4` | `--fry-p-color-bone-10` | `--fry-s-color-surface-system-loading` | Fondo de pantallas de carga global. |
| `surface.state.unselected.default` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-surface-state-unselected-default` | Fondo del control no seleccionado. |
| `surface.state.unselected.hover` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-surface-state-unselected-hover` | Estado hover para fondo del control no seleccionado. |
| `surface.state.unselected.pressed` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-surface-state-unselected-pressed` | Estado pressed fondo del control no seleccionado. |
| `surface.state.selected.default` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-surface-state-selected-default` | Fondo del control seleccionado. |
| `surface.state.selected.hover` | `#2c2f39` | `--fry-p-color-yanbal-black-90` | `--fry-s-color-surface-state-selected-hover` | Estado de hover para fondo del control seleccionado. |
| `surface.state.selected.pressed` | `#414550` | `--fry-p-color-yanbal-black-80` | `--fry-s-color-surface-state-selected-pressed` | Estado pressed para fondo del control seleccionado. |
| `surface.interaction.empty.default` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-surface-interaction-empty-default` | Fondo de zonas interactivas vacías. |
| `surface.interaction.empty.hover` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-surface-interaction-empty-hover` | Estado hover para fondo de zonas interactivas vacías. |
| `surface.interaction.empty.pressed` | `#a1a5ae` | `--fry-p-color-yanbal-black-40` | `--fry-s-color-surface-interaction-empty-pressed` | Estado pressed para fondo de zonas interactivas vacías. |
| `surface.interaction.empty.subtle` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-surface-interaction-empty-subtle` | Fondo de zonas interactivas vacías. |
| `surface.interaction.filled.default` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-surface-interaction-filled-default` | Fondo de zonas interactivas con contenido. |
| `surface.interaction.filled.hover` | `#414550` | `--fry-p-color-yanbal-black-80` | `--fry-s-color-surface-interaction-filled-hover` | Estado hover para fondo de zonas interactivas con contenido. |
| `surface.interaction.filled.pressed` | `#6e727c` | `--fry-p-color-yanbal-black-60` | `--fry-s-color-surface-interaction-filled-pressed` | Estado pressed para fondo de zonas interactivas con contenido. |
| `surface.navigation.active.default` | `#c94e22` | `--fry-p-color-yanbal-orange-80` | `--fry-s-color-surface-navigation-active-default` | Fondo de navegación activo (energizado). |
| `surface.navigation.active.hover` | `#a83c18` | `--fry-p-color-yanbal-orange-90` | `--fry-s-color-surface-navigation-active-hover` | Estado hover para fondo de navegación activo (energizado). |
| `surface.navigation.active.pressed` | `#7a2e14` | `--fry-p-color-yanbal-orange-100` | `--fry-s-color-surface-navigation-active-pressed` | Estado pressed para fondo de navegación activo (energizado). |
| `surface.navigation.inactive.default` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-surface-navigation-inactive-default` | Fondo de navegación disponible pero no activo. |
| `surface.navigation.inactive.hover` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-surface-navigation-inactive-hover` | Estado hover para fondo de navegación disponible pero no activo. |
| `surface.navigation.inactive.pressed` | `#a1a5ae` | `--fry-p-color-yanbal-black-40` | `--fry-s-color-surface-navigation-inactive-pressed` | Estado pressed para fondo de navegación disponible pero no activo. |
| `surface.informative.default` | `#f5f3ef` | `--fry-p-color-pearl-20` | `--fry-s-color-surface-action-tertiary-default` | Fondo para acción informativa |
| `surface.informative.hover` | `#e3e0d5` | `--fry-p-color-pearl-50` | `--fry-s-color-surface-action-tertiary-hover` | Interacción de hover para fondo para acción informativa |
| `surface.informative.pressed` | `#b2afa3` | `--fry-p-color-pearl-80` | `--fry-s-color-surface-action-tertiary-pressed` | Interacción de pressed para fondo para acción informativa |

### 4.3 Border (bordes)

| Token | Hex | Apunta a | Variable CSS | Descripción |
|---|---|---|---|---|
| `border.neutral.strong` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-border-neutral-strong` | Border de alta prominencia. |
| `border.neutral.soft` | `#a1a5ae` | `--fry-p-color-yanbal-black-40` | `--fry-s-color-border-neutral-soft` | Separador suave. |
| `border.neutral.focus` | `#0066bf` | `--fry-p-color-blue-60` | `--fry-s-color-border-neutral-focus` |  |
| `border.neutral.disabled` | `#858993` | `--fry-p-color-yanbal-black-50` | `--fry-s-color-border-neutral-disabled` | Border en estado deshabilitado. |
| `border.neutral.base` | `#575b66` | `--fry-p-color-yanbal-black-70` | `--fry-s-color-border-neutral-base` | Border estándar. |
| `border.neutral.subtle` | `#e6e8ec` | `--fry-p-color-yanbal-black-20` | `--fry-s-color-border-neutral-subtle` | Separador casi imperceptible. |
| `border.feedback.info.soft` | `#0066bf` | `--fry-p-color-blue-60` | `--fry-s-color-border-feedback-info-soft` | Borde de banner informativo. |
| `border.feedback.success.soft` | `#2aa6aa` | `--fry-p-color-mint-60` | `--fry-s-color-border-feedback-success-soft` | Borde de mensaje de éxito. |
| `border.feedback.success.base` | `#1f8084` | `--fry-p-color-mint-80` | `--fry-s-color-border-feedback-success-base` | Borde de mensaje de éxito. |
| `border.feedback.warning.soft` | `#ff9420` | `--fry-p-color-marigold-60` | `--fry-s-color-border-feedback-warning-soft` | Borde de mensaje de advertencia. |
| `border.feedback.danger.soft` | `#e5554f` | `--fry-p-color-crimson-50` | `--fry-s-color-border-feedback-danger-soft` | Borde de mensaje de error. |
| `border.feedback.danger.base` | `#b02b25` | `--fry-p-color-crimson-60` | `--fry-s-color-border-feedback-danger-base` | Borde de mensaje de error. |
| `border.feedback.neutral.strong` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-border-feedback-neutral-strong` | Borde de feedback sin carga. |
| `border.action.secondary.default` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-border-action-secondary-default` | Outline del botón secundario. |
| `border.action.secondary.hover` | `#575b66` | `--fry-p-color-yanbal-black-70` | `--fry-s-color-border-action-secondary-hover` | Estado hover para outline del botón secundario. |
| `border.action.secondary.pressed` | `#858993` | `--fry-p-color-yanbal-black-50` | `--fry-s-color-border-action-secondary-pressed` | Estado pressed para outline del botón secundario. |
| `border.action.secondary.inverse-hover` | `#c4c7ce` | `--fry-p-color-yanbal-black-30` | `--fry-s-color-border-action-secondary-inverse-hover` | Estado hover para outline del botón secundario sobre fondos oscuros |
| `border.action.secondary.inverse` | `#ffffff` | `--fry-p-color-yanbal-black-10` | `--fry-s-color-border-action-secondary-inverse` | Outline del botón secundario sobre fondos oscuros |
| `border.action.secondary.inverse-pressed` | `#858993` | `--fry-p-color-yanbal-black-50` | `--fry-s-color-border-action-secondary-inverse-pressed` | Estado pressed para outline del botón secundario sobre fondos oscuros |
| `border.status.default.soft` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-border-status-default-soft` | Outline de badge  o tag default. |
| `border.status.completed.soft` | `#2eb0b4` | `--fry-p-color-mint-50` | `--fry-s-color-border-status-completed-soft` | Outline de badge  o tag activo o completado |
| `border.status.risk.soft` | `#ff9420` | `--fry-p-color-marigold-60` | `--fry-s-color-border-status-risk-soft` | Outline de badge  o tag inactivo en riesgo o incompleto. |
| `border.status.blocked.soft` | `#e5554f` | `--fry-p-color-crimson-50` | `--fry-s-color-border-status-blocked-soft` | Outline de badge  o tag con deuda o bloqueado |
| `border.status.informative.soft` | `#0066bf` | `--fry-p-color-blue-60` | `--fry-s-color-border-status-informative-soft` | Outline de badge  o tag informativo |
| `border.status.reactivated.soft` | `#81586f` | `--fry-p-color-wine-50` | `--fry-s-color-border-status-reactivated-soft` |  |
| `border.status.reenroll.soft` | `#81586f` | `--fry-p-color-wine-50` | `--fry-s-color-border-status-reactivated-soft` | Outline de badge  o tag potencialmente reincorporable. |
| `border.state.unselected.default` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-border-state-unselected-default` | Outline del control no seleccionado. |
| `border.state.unselected.hover` | `#2c2f39` | `--fry-p-color-yanbal-black-90` | `--fry-s-color-border-state-unselected-hover` | Estado hover para outline del control no seleccionado. |
| `border.state.unselected.pressed` | `#414550` | `--fry-p-color-yanbal-black-80` | `--fry-s-color-border-state-unselected-pressed` | Estado pressed para outline del control no seleccionado. |
| `border.state.inactive.default` | `#1c1f28` | `--fry-p-color-yanbal-black-100` | `--fry-s-color-border-state-inactive-default` | Outline del control inactivo. |
| `border.state.inactive.hover` | `#2c2f39` | `--fry-p-color-yanbal-black-90` | `--fry-s-color-border-state-inactive-hover` | Estado hover para outline del control inactivo. |
| `border.state.inactive.pressed` | `#414550` | `--fry-p-color-yanbal-black-80` | `--fry-s-color-border-state-inactive-pressed` | Estado pressed para outline del control inactivo. |
| `border.state.active.default` | `#c94e22` | `--fry-p-color-yanbal-orange-80` | `--fry-s-color-border-state-active-default` | Outline del control activo. |
| `border.state.active.hover` | `#a83c18` | `--fry-p-color-yanbal-orange-90` | `--fry-s-color-border-state-active-hover` | Estado hover para outline del control activo. |
| `border.state.active.pressed` | `#7a2e14` | `--fry-p-color-yanbal-orange-100` | `--fry-s-color-border-state-active-pressed` | Estado pressed para outline del control activo. |
| `border.system.focus` | `#0066bf` | `--fry-p-color-blue-60` | `--fry-s-color-border-neutral-focus` | Focus ring de accesibilidad |
