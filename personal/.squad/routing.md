# Personal Squad — Routing Rules

## Routing por tipo de trabajo

| Patrón de tarea | Agente asignado | Razón |
|-----------------|-----------------|-------|
| Architecture, system design, RFC | Architect | Technical direction |
| Implementation, features, bugs | Engineer | Hands-on coding |
| Review, security, testing | Reviewer | Quality gate |
| Large features ("team") | All in parallel | Fan-out |

## Escalation

- Security concerns → stop and notify user
- Breaking changes → Architect reviews first
- Ambiguous scope → Architect decomposes
