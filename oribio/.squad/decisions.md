# Oribio Squad — Decisiones

> Estas decisiones son heredadas por todos los repos de Oribio-Co via upstream inheritance.
> Los agentes las leen antes de cada spawn.

---

### 2026-05-06: Stack base de Oribio
**By:** Lead
**What:** Los proyectos de Oribio usan: Vite + Vanilla JS (SuperApp), HTML/CSS estático (Landing), Next.js + TypeScript (Image Creation), TypeScript + MCP SDK (MCP Server), Azure Functions .NET 8 (cart recovery)
**Why:** Stack establecido y productivo — no cambiar sin justificación fuerte

---

### 2026-05-06: Seguridad como prioridad
**By:** Lead
**What:** Todas las implementaciones deben cumplir con las políticas de `Oribio_Security`. Nunca commitear secrets, siempre usar variables de entorno.
**Why:** Política organizacional obligatoria

---

### 2026-05-06: README siempre actualizado
**By:** Lead
**What:** Cada commit a main que cambie funcionalidad, stack, URLs, estructura, comandos o configuración DEBE actualizar el README.md en el mismo commit.
**Why:** El README es la fuente de verdad del proyecto

---

### 2026-05-06: Consultar MCP antes de inventar datos
**By:** Lead
**What:** Cuando se trabaje con datos de negocio (productos, precios, estrategia, marketing), siempre consultar el Oribio MCP Server. No inventar datos.
**Why:** Precisión del negocio es crítica

---

### 2026-05-06: Idioma
**By:** Lead
**What:** Código y variables en inglés. Comentarios y documentación en español (castellano). Respuestas al usuario en el idioma que use.
**Why:** Consistencia con el equipo

---

### 2026-05-06: Calidad visual
**By:** Analyst
**What:** Dashboards y reportes deben: caber en pantalla sin scroll horizontal, incluir conclusiones orientadas a decisiones, usar visualizaciones claras y profesionales.
**Why:** Estándar de UX del equipo
