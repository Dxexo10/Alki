# Alki — Parámetros de Diseño

> Documento de referencia extraído de los archivos reales del prototipo:
> `design-system.css` (fuente autoridad, v2.0) y `shared.js` (interacciones e iconos).
> Todos los valores aquí listados son los que existen hoy en el código; no hay valores inventados.
> Tema: **solo modo claro (light mode)**.

---

## 1. Marca

**Producto:** Alki
**Categoría:** marketplace C2C de alquiler de herramientas y contratación de servicios (Perú — soles, S/).
**Tagline (splash `index.html`):** «Alquila, ofrece, conéctate.»

### Paleta "Holst" (rampa cruda)

| Variable | Hex | Uso principal |
|---|---|---|
| `--holst-1` | `#223A5E` | Texto principal, headers oscuros, `--brand-primary-dark` |
| `--holst-2` | `#355982` | Texto secundario, extremo oscuro de gradientes de avatar/foto |
| `--holst-3` | `#4D79A8` | Texto terciario, acento de marca (`--brand-accent`), gradientes |
| `--holst-4` | `#6E9ECC` | Azul medio de la rampa, orbes y gradientes decorativos |
| `--holst-5` | `#9FC0E3` | Texto placeholder, iconos inactivos, extremo claro de gradientes |
| `--holst-6` | `#D0E1F2` | Superficies secundarias (`--bg-tertiary`), bordes neutros (`--border-default`) |
| `--holst-7` | `#F3F8FD` | Fondo de la app (`--bg-primary`) |

Rampa completa (según comentario del header del CSS):
`#223A5E · #355982 · #4D79A8 · #6E9ECC · #9FC0E3 · #D0E1F2 · #F3F8FD`

### Logo

Construido en `index.html`, en dos partes:

- **Ícono / marca (`.splash-logo-mark`):** SVG inline de 48×48 px dentro de un tile cuadrado redondeado de 88×88 px con radio `--radius-2xl` (24px). El dibujo es un "pin/ubicación" con un círculo de trazo discontinuo (`stroke-dasharray="2 2"`) y una X interior (combo pin + herramienta/servicio). Trazo `stroke="currentColor"`, `stroke-width="2"`, esquinas y extremos redondeados. El tile usa efecto vidrio (ver §3): `background: rgba(243, 248, 253, 0.12)`, `backdrop-filter: blur(20px)`, `border: 1px solid rgba(243, 248, 253, 0.25)`, `box-shadow: 0 12px 32px rgba(34, 58, 94, 0.35)`.
- **Wordmark:** `Alki` en una tipografía **Fraunces** (`--font-display`), manteniendo el tratamiento de dos segmentos (adaptado a un nombre corto):
  - «Al» → Fraunces **700**, sin cursiva, color `--text-on-brand` (`#FFFFFF`).
  - «ki» → envuelto en `<span>`, Fraunces **400 en cursiva**, color `--holst-5` (`#9FC0E3`).
  - En el splash el título mide **38px**, `letter-spacing: var(--tracking-tight)` (−0.04em), `line-height: var(--leading-tight)` (1.05).
  - El design system también expone la clase reutilizable `.logo-wordmark` (Fraunces, `font-weight: 700`, `tracking-tight`, `leading-tight`).

---

## 2. Tipografía

### Familias

| Rol | Variable | Familia | Fallbacks |
|---|---|---|---|
| Display / branding (títulos, wordmark, precios, "Hola, Diego") | `--font-display` | **Fraunces** (serif) | `Georgia, serif` |
| Cuerpo / UI | `--font-ui` | **Manrope** | `-apple-system, BlinkMacSystemFont, system-ui, sans-serif` |

**Import exacto de Google Fonts** (primera línea de `design-system.css`):

```css
@import url('https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,400;0,9..144,500;0,9..144,600;0,9..144,700;1,9..144,300;1,9..144,400;1,9..144,600&family=Manrope:wght@300;400;500;600;700&display=swap');
```

### Escala de tamaños

| Token | Valor | Uso típico |
|---|---|---|
| `--text-xs` | 11px | Chips, labels auxiliares, texto legal, meta |
| `--text-sm` | 13px | Texto de ayuda, subtítulos secundarios, mensajes de error |
| `--text-base` | 15px | Cuerpo de texto, inputs, textos de párrafo |
| `--text-md` | 17px | Títulos de sección / nav, texto de botones |
| `--text-lg` | 20px | Saludo destacado, encabezados de bloque |
| `--text-xl` | 24px | Título de modal |
| `--text-2xl` | 28px | Encabezados grandes |
| `--text-3xl` | 34px | Título de pantalla |
| `--text-hero` | 42px | Hero / máximo énfasis |

### Interlineado y tracking

| Line-height | Valor | | Letter-spacing | Valor |
|---|---|---|---|---|
| `--leading-tight` | 1.05 | | `--tracking-tight` | −0.04em |
| `--leading-snug` | 1.2 | | `--tracking-snug` | −0.02em |
| `--leading-normal` | 1.4 | | `--tracking-normal` | 0em |
| `--leading-relaxed` | 1.6 | | `--tracking-wide` | 0.02em |
| | | | `--tracking-wider` | 0.06em |
| | | | `--tracking-widest` | 0.10em |

Convención observada: los títulos usan `tracking-tight` (−0.04em) o `tracking-snug` (−0.02em); el cuerpo usa `tracking-normal`; los chips y etiquetas pequeñas usan `tracking-wide` (0.02em).

### Pesos

Disponibles: **300, 400, 500, 600, 700** (Fraunces además tiene itálicas 300/400/600).

- **400 (regular):** cuerpo de texto, párrafos, "ki" en cursiva.
- **500 (medium):** segmentos de control no activos, texto secundario/ayuda.
- **600 (semibold):** botones, chips, títulos de sección, nav, labels de formulario.
- **700 (bold):** wordmark, títulos display, iniciales de avatar, saludo, precios destacados.

---

## 3. Color y superficies

### Superficies

| Variable | Hex | Uso |
|---|---|---|
| `--bg-primary` | `#F3F8FD` | Fondo base de la app |
| `--bg-secondary` | `#FFFFFF` | Cards, sheets, modales |
| `--bg-tertiary` | `#D0E1F2` | Estados presionados, superficies secundarias |
| `--bg-elevated` | `#FFFFFF` | Modales, popovers |

### Texto

| Variable | Hex | Uso |
|---|---|---|
| `--text-primary` | `#223A5E` | Texto principal |
| `--text-secondary` | `#355982` | Texto secundario |
| `--text-tertiary` | `#4D79A8` | Texto terciario / atenuado |
| `--text-placeholder` | `#9FC0E3` | Placeholders, iconos inactivos |
| `--text-on-brand` | `#FFFFFF` | Texto sobre fondos de marca |
| `--text-on-dark` | `#F3F8FD` | Texto sobre superficies oscuras |

### Marca / interactivo

| Variable | Hex / valor | Uso |
|---|---|---|
| `--brand-primary` | `#355982` | Acción principal, links, tab activo |
| `--brand-primary-dark` | `#223A5E` | Variante oscura de marca |
| `--brand-primary-light` | `#4D79A8` | Variante clara de marca |
| `--brand-accent` | `#4D79A8` | Acento |
| `--brand-accent-soft` | `rgba(77, 121, 168, 0.10)` | Fondo tenue de acento (chips/foco) |

### Estados semánticos

| Variable | Hex / valor | Uso |
|---|---|---|
| `--brand-error` | `#C0392B` | Error / inválido |
| `--brand-error-soft` | `rgba(192, 57, 43, 0.10)` | Fondo tenue de error |
| `--brand-success` | `#1B9E4B` | Éxito / "Disponible" / verificado |
| `--brand-success-soft` | `rgba(27, 158, 75, 0.10)` | Fondo tenue de éxito |
| `--brand-warning` | `#B86D00` | Advertencia / estrellas de rating / pendiente |
| `--brand-warning-soft` | `rgba(184, 109, 0, 0.10)` | Fondo tenue de advertencia |
| `--brand-info` | `#355982` | Información |

### Bordes y separadores

| Variable | Valor | Uso |
|---|---|---|
| `--separator` | `rgba(34, 58, 94, 0.10)` | Separadores internos (filas, dividers) |
| `--separator-strong` | `rgba(34, 58, 94, 0.20)` | Separador reforzado |
| `--border-default` | `#D0E1F2` | Borde neutro por defecto de inputs/campos |
| `--border-focus` | `#355982` | Borde de foco |

### Sombras

| Variable | Valor |
|---|---|
| `--shadow-xs` | `0 1px 2px rgba(34, 58, 94, 0.06)` |
| `--shadow-sm` | `0 2px 6px rgba(34, 58, 94, 0.08), 0 1px 2px rgba(34, 58, 94, 0.05)` |
| `--shadow-md` | `0 4px 16px rgba(34, 58, 94, 0.10), 0 1px 4px rgba(34, 58, 94, 0.06)` |
| `--shadow-lg` | `0 8px 32px rgba(34, 58, 94, 0.14), 0 2px 8px rgba(34, 58, 94, 0.08)` |
| `--shadow-card` | `0 2px 12px rgba(34, 58, 94, 0.08)` |

### Efecto "liquid glass" (chrome translúcido)

Tokens de material:

| Variable | Valor |
|---|---|
| `--material-thin` | `rgba(243, 248, 253, 0.72)` |
| `--material-regular` | `rgba(243, 248, 253, 0.85)` |
| `--material-thick` | `rgba(243, 248, 253, 0.94)` |
| `--material-dark` | `rgba(34, 58, 94, 0.70)` |
| `--header-bg` | `rgba(243, 248, 253, 0.88)` |
| `--tabbar-bg` | `rgba(243, 248, 253, 0.88)` |

Especificación implementada por superficie:

- **Nav header (`.nav-header`):** `background: var(--header-bg)` (`rgba(243,248,253,0.88)`); `backdrop-filter: blur(20px) saturate(180%)` (+ prefijo `-webkit-`); `border-bottom: 1px solid var(--separator)`.
- **Tab bar (`.tab-bar`):** `background: linear-gradient(to bottom, rgba(243, 248, 253, 0.55), rgba(243, 248, 253, 0.72))`; `backdrop-filter: blur(24px) saturate(180%)`; `border-top: 1px solid rgba(255, 255, 255, 0.55)`; `box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.70), 0 -8px 28px rgba(34, 58, 94, 0.10)`.
- **Bottom action bar (`.bottom-action-bar`):** `background: linear-gradient(to bottom, rgba(243, 248, 253, 0.58), rgba(243, 248, 253, 0.74))`; `backdrop-filter: blur(24px) saturate(180%)`; `border-top: 1px solid rgba(255, 255, 255, 0.55)`; mismo `box-shadow` que la tab bar.
- **Variantes oscuras / sobre foto (splash):** tile de logo `rgba(243,248,253,0.12)` + `blur(20px)`; chips `rgba(34,58,94,0.45)` + `blur(12px)` con borde `rgba(243,248,253,0.38)` y sombra `0 2px 8px rgba(34,58,94,0.25)`.

---

## 4. Componentes base

### Botones (`.btn`)

Base: `display: flex`, centrado, `border-radius: var(--radius-lg)` (16px), `height: 54px`, `width: 100%`, `font-weight: 600`, `font-size: var(--text-md)` (17px), `letter-spacing: var(--tracking-snug)` (−0.02em). Incluye un brillo interno superior (`::before`) con `linear-gradient(to bottom, rgba(255,255,255,0.10), transparent)`.

| Variante | Fondo | Texto | Sombra / borde |
|---|---|---|---|
| `.btn-primary` | `--brand-primary` `#355982` | `--text-on-dark` `#F3F8FD` | `0 4px 20px rgba(53, 89, 130, 0.40), 0 1px 4px rgba(0,0,0,0.10)` |
| `.btn-secondary` | `--bg-tertiary` `#D0E1F2` | `--brand-primary` `#355982` | `--shadow-sm` |
| `.btn-ghost` | transparente | `--brand-primary` | borde `1.5px solid var(--brand-primary)` |
| `.btn-danger` | transparente | `--brand-error` | borde `1.5px solid var(--brand-error)` |

- **Estado presionado:** `.btn:active { transform: scale(0.97); }` (`.btn-primary:active` reduce la sombra).
- **Tamaño pequeño:** `.btn-sm` → `height: 40px`, `font-size: var(--text-sm)`, `border-radius: var(--radius-md)`.
- Nota: algunos formularios (p. ej. `07-publicar-solicitud.html`) redefinen `.btn` localmente con `padding: 14px` y `border-radius: 12px`.

### Tarjetas

- `.card`: `background: var(--bg-secondary)`, `border-radius: var(--radius-xl)` (20px), `box-shadow: var(--shadow-card)`, `overflow: hidden`.
- `.card-grouped`: igual sin sombra.
- `.card-row`: `padding: 14px var(--sp-4)`, `gap: var(--sp-3)`, `min-height: 56px`, `border-bottom: 1px solid var(--separator)`.
- En pantallas de formulario, `.form-group` usa `border-radius: 16px`, `padding: 16px`, `background: var(--bg-secondary)`.

### Chips / pills (`.chip`)

Base: `border-radius: var(--radius-full)`, `padding: 4px 12px`, `font-size: var(--text-xs)` (11px), `font-weight: 600`, `letter-spacing: var(--tracking-wide)` (0.02em).

| Variante | Fondo | Texto |
|---|---|---|
| `.chip-brand` | `--brand-accent-soft` | `--brand-accent` |
| `.chip-success` | `--brand-success-soft` | `--brand-success` |
| `.chip-warning` | `--brand-warning-soft` | `--brand-warning` |
| `.chip-error` | `--brand-error-soft` | `--brand-error` |
| `.chip-muted` | `--bg-tertiary` | `--text-tertiary` |
| `.chip-primary` | `--brand-primary` | `--text-on-dark` |

Chips de filtro de la home (`.cat-chip`, `.scroll-chip`) usan el mismo lenguaje: activo con `--brand-accent-soft` + borde/texto `--brand-primary`; inactivo neutro.

### Control segmentado (`.seg-control`)

Contenedor `--bg-tertiary` con `border-radius: var(--radius-full)` y `padding: 3px`; la opción activa (`.seg-control input:checked + label`) usa `background: var(--bg-secondary)`, `color: var(--brand-primary)` y `--shadow-sm`.

### Iconografía

- Set **propio** (registro inline en `shared.js`): ~46 iconos SVG de trazo, estilo *outline* tipo Phosphor/Lucide, expuestos vía `window.rsIcon(name, className)`.
- Estilo: `fill="none"`, `stroke="currentColor"`, **`stroke-width: 1.8`**, `stroke-linecap: round`, `stroke-linejoin: round`. (El comentario del registro menciona 1.75px, pero el valor real en el código es 1.8.)
- Ajustes por contexto: iconos de tab bar `stroke-width: 1.8` (activo `2.2`); badge verificado `2.5`; iconos usados dentro de textos suelen ir a `2`.
- Tamaños típicos: 12 / 14 / 16 / 18 / 24 px según ubicación.

---

## 5. Espaciado y forma

### Radios de esquina

| Token | Valor | Uso típico |
|---|---|---|
| `--radius-xs` | 4px | Detalles mínimos |
| `--radius-sm` | 8px | Inputs/chips pequeños, botones compactos |
| `--radius-md` | 12px | Botones pequeños, contenedores intermedios |
| `--radius-lg` | 16px | **Botones estándar**, bloques de formulario |
| `--radius-xl` | 20px | **Cards** |
| `--radius-2xl` | 24px | Tile de logo, bloques grandes |
| `--radius-3xl` | 32px | Superficies muy redondeadas |
| `--radius-full` | 9999px | Pills, avatares, toggles |

### Sistema de espaciado

Escala de **4px** (múltiplos), en tokens `--sp-*`:

`--sp-1: 4` · `--sp-2: 8` · `--sp-3: 12` · `--sp-4: 16` · `--sp-5: 20` · `--sp-6: 24` · `--sp-8: 32` · `--sp-10: 40` · `--sp-12: 48` · `--sp-16: 64` px.

**Chrome iOS del mockup:** `--statusbar-height: 54px`, `--header-height: 56px`, `--tabbar-height: 83px`, `--safe-bottom: 34px`.

### Avatares

`.avatar` = círculo (`--radius-full`) con relleno en gradiente `linear-gradient(135deg, var(--holst-3), var(--holst-2))` y texto blanco en negrita. Tamaños: `sm` 32, `md` 44, `lg` 56, `xl` 80, `2xl` 96 px. Modificadores de gradiente: `avatar-gradient-1..4` (de `#355982→#4D79A8`, `#4D79A8→#6E9ECC`, `#223A5E→#355982`, `#6E9ECC→#9FC0E3`).

---

## 6. Movimiento

- **Física de resorte:** curva principal `cubic-bezier(0.34, 1.56, 0.64, 1)` (rebote suave) aplicada a entradas de marca (logo, título, tagline, chips — 520–1000ms), al indicador de tabs y al pulgar del toggle. Cards entran con `cubic-bezier(0.22, 1, 0.36, 1)` a 620ms; las transiciones de pantalla usan `cubic-bezier(0.4, 0, 0.2, 1)` a 280ms (view transitions con dirección forward/back).
- **Micro-interacciones:** 100–200ms — `:active` escala a `0.92`–`0.97`, color de fondo/estado en 150–200ms.
- **Principios (2–3 líneas):** sigue el enfoque de Apple — *feedback inmediato* (todo elemento tocable responde al instante con un scale), *interrumpibilidad y continuidad espacial* (transiciones de navegación cortas y direccionales) y *movimiento con física* (resortes en vez de linear). Todo respeta `@media (prefers-reduced-motion: reduce)`, sustituyendo animaciones por fade de 150–200ms.

---

## 7. Tono de marca (para copy de la landing)

El tono es **cercano y directo, en segunda persona ("tú"/"tu")**, con frases cortas y verbos de acción: «Alquila, ofrece, conéctate», «Publica tu solicitud y recibe ofertas en minutos», «Empieza a ganar con Alki», «¡Cuenta creada! … Tu cuenta está lista». No es técnico ni corporativo, y prácticamente no usa humor: prioriza **claridad y confianza** (transparencia en pagos: «Tu dinero queda retenido en una cuenta de garantía y solo se libera…»). Usa español neutro con localismos peruanos («gasfitería», S/ soles) y refuerza la promesa de seguridad ("Custodia segura Alki", "verificado").

---

## Uso sugerido en landing page

- **Trasladar tal cual:** la paleta Holst completa, la pareja tipográfica (Fraunces para títulos/wordmark, Manrope para UI y cuerpo) con su import de Google Fonts, y el efecto **liquid glass** aplicado al header de la landing (mismo `backdrop-filter: blur(20px) saturate(180%)`, fondo `rgba(243,248,253,0.88)` y borde inferior `--separator`) para que la barra de navegación se sienta idéntica a la del mockup.
- **Adaptar para escritorio:** subir la escala tipográfica de display (el `--text-hero` de 42px es techo de móvil; un hero de landing admite 56–72px en Fraunces), ampliar paddings fuera de la escala compacta `--sp-*`, y usar radios más generosos en las secciones grandes (llevar `--radius-xl`/`--radius-2xl` hacia 24–32px).
- **Reutilizar como componentes:** botones (`--primary`/`--secondary` con `border-radius: 16px` y `:active` scale 0.97), cards con `--shadow-card`, chips de estado (`--success` "Disponible", `--warning` "pendiente", `--muted`) y los gradientes de avatar para testimonios/proveedores.
- **Mantener la conversión:** repetir el patrón del splash (tile de vidrio con el ícono pin+herramienta, wordmark `Al`/`ki` con "ki" en cursiva `--holst-5`, tagline) y conservar el tono de copy cercano y de confianza, evitando lenguaje técnico.
