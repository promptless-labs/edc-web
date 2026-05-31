---
name: edc-security-scalability
description: Security & scalability skill – the only rule active today is "no secrets in client-side code". The rest (auth, admin, abuse, cost amplification, rollback) is FUTURE guidance for when EDC adds a backend.
---

# Security & Scalability Skill (EDC)

> **Estado actual: parcialmente aplicable.** Hoy EDC es estático y sin backend, así que **la regla activa es: cero secretos en el cliente**. Autenticación, rutas admin, control de abuso, amplificación de coste y rollback de backend son guía para *cuando* exista backend.

## Activo hoy (sitio estático)

- **Sin secretos en el repo ni en el cliente.** Todo HTML/JS/config se sirve al navegador: nunca incrustes claves, tokens ni credenciales. Trátalos como públicos.
- **Enlaces de afiliado**: deben llevar su descargo visible (ya presente en `index.html`). No usar tracking invasivo sin aprobación.
- **Recursos de terceros** (Tailwind CDN, Google Fonts, Material Symbols): cargarlos desde orígenes confiables. Si más adelante se endurece la seguridad, considerar CSP/SRI.
- **Rollback**: al ser estático, revertir = volver al artefacto/commit anterior. Mantén los cambios reversibles.

## Futuro (cuando haya backend — ver también edc-backend)

- Autenticación/autorización y rutas admin: **fail closed**; nunca conceder acceso por configuración faltante.
- Validar y acotar entrada no confiable antes de usarla en almacenamiento, fetches, logs o respuestas.
- Revisar rutas de abuso: peticiones repetidas, payloads grandes, queries sin límite, escrituras de alta cardinalidad.
- No registrar datos sensibles; minimizar contexto en logs.
- Considerar amplificación de coste (lecturas/escrituras, llamadas a APIs externas, reintentos).
- Notas de rollback para cualquier cambio que afecte producción, datos, acceso o coste.

## Output

- **Critical risks** primero (exposición de secretos sobre todo).
- Findings por severidad, mitigaciones requeridas, checklist de validación manual y notas de rollback.
