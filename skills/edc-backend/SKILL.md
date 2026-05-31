---
name: edc-backend
description: Backend skill (FUTURE / not yet applicable) – guidance for if/when EDC adds serverless functions, API routes, storage, or form handling. The site is currently 100% static.
---

# Backend Skill (EDC) — reservada para el futuro

> **Estado actual: NO APLICA.** EDC es hoy un sitio 100% estático (HTML + Tailwind Play CDN), **sin backend**. No hay funciones serverless, rutas de API ni base de datos. Esta skill es guía para *cuando* se añada backend; no inventes uno por iniciativa propia.

## Cuándo activar esta skill

Solo cuando el usuario pida explícitamente añadir capacidades dinámicas, por ejemplo:

- Un endpoint para el formulario de newsletter/contacto.
- Persistir o leer datos (suscriptores, métricas).
- Cualquier lógica que no pueda vivir solo en el cliente.

## Recomendaciones de partida (cuando llegue el momento)

- **Antes de elegir stack, pregunta al usuario.** Para un sitio estático, lo más barato suele ser un servicio externo (formularios de terceros, p. ej. Formspree/Resend) en vez de montar backend propio.
- Si se necesita backend propio, preferir una opción serverless de bajo coste acorde al hosting estático elegido.
- Validar **toda** entrada externa (método, content-type, tamaño, campos requeridos, tipos, enums) con allowlists explícitas.
- Respuestas con manejo de errores claro, mensajes seguros y códigos de estado correctos. Nunca filtrar internals.
- Vigilar coste y rate-limits: bucles, fetches sin límite, escrituras de alta cardinalidad.
- No introducir dependencias que no encajen con el runtime de despliegue.

## Output

- Findings, archivos a tocar, riesgos (compatibilidad de runtime, contrato de API, coste, rate-limit) y comandos de verificación.
- Mientras el sitio siga siendo estático, lo correcto suele ser **proponer la alternativa sin backend** y confirmar con el usuario antes de añadir infraestructura.
