# AI Development Guidelines (Canonical)

This document is the single source of truth for how AI tools (Claude, Codex, Copilot, etc.) and human contributors collaborate in this repository.

These rules apply to the entire repository unless a more specific `AGENTS.md` or doc overrides them locally.

---

## Project Snapshot

- **Project**: EDC — "El Dinero Es Claro", web de educación financiera.
- **Stack**: HTML estático + Tailwind CSS. **Sin framework** (no Astro, no React, no SSR).
- **Tailwind**: vía **Play CDN** (`<script src="https://cdn.tailwindcss.com">`). **No hay paso de build**: sin Tailwind CLI, sin PostCSS, sin `package.json`, sin CSS compilado.
- **Configuración de Tailwind**: inline en cada HTML, en un `<script id="tailwind-config">` (`tailwind.config = { ... }`).
- **Languages**: HTML, CSS (utilidades Tailwind + `<style>` inline puntual), JavaScript de cliente mínimo y solo si es imprescindible.
- **Idioma del sitio**: Solo español (una sola versión, sin rutas por idioma ni hreflang).
- **Backend**: **Ninguno actualmente.** El sitio es 100% estático. Hay skills de backend/seguridad pensadas para el futuro, marcadas como "no aplica todavía".
- **Deployment**: Hosting estático (sirve HTML/CSS/JS tal cual).

---

## Design Tokens (paleta oficial)

Colores base del proyecto:

| Token        | Hex       | Uso                                   |
| ------------ | --------- | ------------------------------------- |
| Fondo        | `#0A0A0A` | Fondo principal (tema oscuro)         |
| Acento verde | `#00C853` | CTA, enlaces, énfasis, iconos         |
| Texto        | `#FFFFFF` | Texto principal sobre fondo oscuro    |

Cómo se aplican hoy en `index.html`:

- El fondo se aplica con la utilidad arbitraria `bg-[#0A0A0A]` en `<body>`.
- El acento `#00C853` ya existe en la `tailwind.config` inline como el token `primary-container`; en el markup se usa tanto `text-[#00C853]` como `bg-primary-container`.
- El texto principal usa `text-[#FFFFFF]` / `text-white`.

Reglas:

- **Tema oscuro único.** No hay toggle claro/oscuro (aunque exista `darkMode: "class"` y la clase `dark` en `<html>`).
- El verde `#00C853` es **acento**: úsalo para acción y énfasis, no como fondo de áreas grandes.
- Preferible centralizar los colores en la `tailwind.config` inline como tokens con nombre en vez de repetir hex arbitrarios (`#111111`, `#888888`, `#1A1A1A`, `#2A2A2A`…). Al añadir secciones, reutiliza los tokens existentes antes de inventar nuevos hex.

---

## Repository Layout (High Level)

Sitio estático servido tal cual; sin carpeta de build.

```
edc-web/
├─ index.html         # Página principal (Tailwind Play CDN + config inline)
├─ *.html             # Páginas adicionales a medida que se creen
├─ assets/            # Imágenes, íconos, etc. (crear cuando se necesite)
├─ docs/              # Documentación del proyecto (este archivo vive aquí)
├─ skills/            # Skills de contexto para asistentes de IA
├─ .claude/           # Comandos y settings de Claude Code
├─ AGENTS.md          # Adapter para agentes tipo Codex
├─ CLAUDE.md          # Adapter para Claude
└─ README.md
```

- No existe `node_modules`, ni `dist/`, ni CSS generado: con Play CDN, Tailwind se compila en el navegador.

---

## Core Rules

1. **Lee antes de editar.** Revisa el HTML/doc relevante antes de cambiar nada.
2. **Cambios mínimos y acotados** al pedido del usuario. Diffs pequeños y específicos.
3. **No frameworks ni build.** No introduzcas Astro/React/Vue, bundlers, Tailwind CLI/PostCSS ni `package.json` sin que se pida explícitamente. Mantén Play CDN salvo decisión contraria del usuario.
4. **No backend.** Hoy es un sitio estático. No agregues funciones serverless, rutas de API ni lógica de servidor a menos que se pida (ver skills de backend/seguridad, marcadas como futuro).
5. **Usa la paleta oficial** y, cuando sea práctico, tokens con nombre en la `tailwind.config` inline en vez de hex sueltos.
6. **Accesibilidad (WCAG AA)** como requisito: contraste sobre `#0A0A0A`, foco visible, navegación por teclado, HTML semántico. Cuida los iconos de Material Symbols (texto alternativo / `aria-hidden` cuando sean decorativos).
7. **Español.** Todo el contenido visible va en español.
8. **Sin secretos.** Un sitio estático sirve todo al cliente; nunca incrustes claves, tokens ni credenciales. Los enlaces de afiliado deben llevar su descargo correspondiente.
9. **Indentación.** Todo el HTML debe estar correctamente indentado: 2 espacios por nivel, elementos anidados un nivel más profundo que su padre. El código JavaScript dentro de `<script>` también se indenta. Usa `npx prettier --write <archivo> --print-width 200 --tab-width 2 --html-whitespace-sensitivity ignore` para formatear. No dejes HTML plano sin indentar.

---

## Role Skills

Las skills en `skills/` dan contexto especializado por área. Cada una tiene un comando equivalente en `.claude/commands/`.

- **edc-frontend** — HTML, Tailwind (Play CDN + config inline), accesibilidad, responsive, rendimiento, paleta. *(Activa hoy.)*
- **edc-seo** — metadata, canonical, Open Graph/Twitter, JSON-LD, sitemap, robots (sitio en español, sin hreflang). *(Activa hoy.)*
- **edc-backend** — funciones/API/almacenamiento. *(No aplica todavía: el sitio no tiene backend. Guía para cuando se añada.)*
- **edc-security-scalability** — secretos, auth, abuso, coste, rollback. *(Hoy solo aplica la regla "sin secretos en el cliente"; el resto es guía para cuando haya backend.)*

---

## Snapshot (shared block)

<!-- BEGIN AGENTS-BASE -->
EDC — "El Dinero Es Claro", web de educación financiera en español. Stack: HTML estático + Tailwind CSS vía Play CDN (config inline en el HTML, sin build, sin framework, sin backend). Tema oscuro único; paleta: fondo `#0A0A0A`, acento verde `#00C853`, texto `#FFFFFF`. Deploy en hosting estático. Reglas clave: cambios mínimos, sin frameworks/build/backend, usar la paleta oficial, accesibilidad WCAG AA, contenido en español, sin secretos en el cliente. Las skills edc-backend y edc-security-scalability están reservadas para el futuro (aún no hay backend).
<!-- END AGENTS-BASE -->
