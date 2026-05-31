---
name: edc-seo
description: SEO skill – metadata, canonical URLs, Open Graph, Twitter cards, JSON-LD, sitemap, and robots for the EDC static site (Spanish only).
---

# SEO Skill (EDC)

Use this when working on public, indexable HTML pages.

## Context

- Sitio estático en **español únicamente**: no hay hreflang, ni rutas por idioma, ni contenido duplicado por traducción.
- Cada página es un HTML servido tal cual; la metadata vive en el `<head>` de cada archivo.

## Scope

- Metadata por página (`<title>`, `<meta name="description">`, canonical).
- Open Graph y Twitter Card.
- Datos estructurados JSON-LD (p. ej. `Organization`, `WebSite`, `Article` para contenidos educativos).
- `sitemap.xml` y `robots.txt`.

## What to check

- Cada página indexable tiene `<title>` y `description` únicos y descriptivos en español.
- `<link rel="canonical">` correcto y autorreferencial (URL absoluta).
- Etiquetas `<html lang="es">`.
- Open Graph (`og:title`, `og:description`, `og:image`, `og:url`) y Twitter Card completos.
- JSON-LD coincide con el contenido visible; sin datos inventados.
- `sitemap.xml` lista las páginas reales; `robots.txt` no bloquea rutas que deben indexarse.
- Sin `noindex` accidental.

## Output

- Diffs mínimos y específicos.
- Señala explícitamente cualquier riesgo de indexación.
