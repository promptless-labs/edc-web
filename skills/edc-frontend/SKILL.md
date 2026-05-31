---
name: edc-frontend
description: Frontend skill – static HTML, Tailwind via Play CDN with inline config, design tokens (palette), accessibility, responsive behavior, and frontend performance for the EDC site.
---

# Frontend Skill (EDC)

Use this when working on the user-facing UI: HTML pages and Tailwind styles. **Esta es la skill principal y activa del proyecto.**

## Stack

- **HTML estático, sin framework.** No hay routing de cliente ni componentes; las páginas son archivos `.html`.
- **Tailwind vía Play CDN**: `<script src="https://cdn.tailwindcss.com">`. **No hay build** (ni Tailwind CLI, ni PostCSS, ni `package.json`).
- **Config inline**: la `tailwind.config` vive en un `<script id="tailwind-config">` dentro del `<head>` de cada HTML (colores, `fontFamily`, `spacing`, etc.). Edítala ahí.
- Estilos puntuales en un `<style>` inline (p. ej. `.edc-card`). Iconos con **Material Symbols Outlined**; tipografía **Inter**.
- JavaScript de cliente solo cuando sea imprescindible y progresivo (la página debe funcionar sin JS).

## Paleta oficial

| Color        | Hex       | Notas                                                        |
| ------------ | --------- | ------------------------------------------------------------ |
| Fondo        | `#0A0A0A` | `bg-[#0A0A0A]` en `<body>`; secciones alternan con `#111111` |
| Acento verde | `#00C853` | `text-[#00C853]` o token `primary-container`; iconos en verde |
| Texto        | `#FFFFFF` | `text-white` / `text-[#FFFFFF]`; texto secundario `#888888`  |

- Tema oscuro único; el verde es acento, no fondo de grandes áreas.
- Prefiere tokens con nombre en la `tailwind.config` inline antes que repetir hex arbitrarios.

## What to check

- HTML semántico (`header`, `nav`, `main`, `section`, `footer`, encabezados en orden) en español.
- Colores coherentes con la paleta; reutiliza tokens/clases existentes antes de añadir hex nuevos.
- Contraste WCAG AA sobre `#0A0A0A`; ojo con el texto `#888888` sobre fondo oscuro en textos pequeños.
- Foco visible y navegación por teclado en enlaces y botones; iconos decorativos con `aria-hidden`.
- Layout responsive (mobile-first) con utilidades Tailwind; sin desbordes horizontales; respeta `max-w-[1200px]`.
- Rendimiento: imágenes optimizadas con `width`/`height`, JS mínimo. (Nota: Play CDN no es ideal para producción a gran escala; si el rendimiento importa, plantear al usuario migrar a un build — no hacerlo por iniciativa propia.)
- Markup repetido (tarjetas, secciones) consistente; evita copiar-pegar divergente.

## Output

- Diffs mínimos y específicos.
- Señala explícitamente cualquier regresión de accesibilidad, contraste o rendimiento.
