# Oribio Squad — Routing Rules

## Routing por tipo de trabajo

| Patrón de tarea | Agente asignado | Razón |
|-----------------|-----------------|-------|
| Dashboard, analytics, métricas, KPIs | Analyst | Especialista en datos |
| API, backend, endpoints, Azure Functions | Builder | Full-stack implementación |
| UI, landing, componentes, diseño | Builder | Full-stack implementación |
| Tests, QA, validación, edge cases | Tester | Calidad |
| Arquitectura, decisiones, refactor grande | Lead | Scope y dirección |
| Shopify, productos, inventario | Builder + Analyst | Implementación + insights |

## Fan-out rules

- Palabra clave "team" → todos los agentes trabajan en paralelo
- Nombre específico de agente → solo ese agente
- Tareas ambiguas → Lead descompone y asigna

## Escalation

- Si un agente encuentra conflicto con decisión existente → escalar a Lead
- Si se detecta posible issue de seguridad → parar y notificar al usuario
- Si se necesita dato de negocio → consultar MCP Server primero
