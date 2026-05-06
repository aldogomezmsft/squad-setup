# Squad Setup — Multi-Agent Orchestration

> **Status:** Implementación activa · Squad está en alpha (experimental)

Configuración y documentación de [Squad](https://bradygaster.github.io/squad/) para orquestación multi-agente en dos contextos:

- **Oribio-Co** — Org-level Squad para todos los repos de Oribio
- **Personal (aldogomezmsft)** — Squad global para proyectos de Microsoft

## ¿Qué es Squad?

Squad es un framework de orquestación multi-agente que coordina agentes especializados (roles) dentro de tu repo. Cada agente tiene su carta de servicio, memoria persistente, y respeta decisiones acumuladas del equipo.

### Características clave

| Feature | Descripción |
|---------|-------------|
| **Multi-agente paralelo** | Múltiples agentes trabajan simultáneamente en tareas descompuestas |
| **Memoria persistente** | Decisiones y convenciones persisten entre sesiones |
| **GitHub-Native** | Vive en `.squad/` — se commitea, clona y comparte |
| **Gobernanza** | File-write guards, PII scrubbing, reviewer lockout |
| **SDK tipado** | Configuración en TypeScript con `squad.config.ts` |
| **Upstream Inheritance** | Herencia de contexto entre repos/orgs |

## Cómo complementa nuestro setup actual

```
┌─────────────────────────────────────────────────────────────┐
│                    ANTES (actual)                             │
├─────────────────────────────────────────────────────────────┤
│  copilot-instructions.md  →  Un solo agente con contexto     │
│  Oribio-MCP-Server        →  Base de conocimiento (31+ docs) │
│  Oribio_Security           →  Políticas (markdown manual)     │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│                    DESPUÉS (con Squad)                        │
├─────────────────────────────────────────────────────────────┤
│  .squad/                   →  Equipo multi-agente coordinado  │
│  Oribio-MCP-Server        →  Conocimiento (sin cambio)       │
│  copilot-instructions.md  →  Se mantiene como base            │
│  upstream inheritance      →  Org hereda a todos los repos    │
│  Gobernanza automática     →  Guards enforced en código        │
└─────────────────────────────────────────────────────────────┘
```

### Diferencias con el approach actual

| Aspecto | Antes | Con Squad |
|---------|-------|-----------|
| Agentes | 1 (Copilot con instrucciones) | N agentes especializados en paralelo |
| Memoria | MCP server (estática) | `.squad/decisions.md` + agent histories (acumulativa) |
| Gobernanza | Documentada en markdown | Enforced programáticamente |
| Coordinación | Manual (usuario dirige todo) | Coordinador automático descompone y asigna |
| Scope | Por repo | Herencia org → team → repo |

## Estructura del repo

```
squad-setup/
├── README.md                    # Este archivo
├── docs/
│   ├── architecture.md          # Diagrama de arquitectura
│   ├── comparison.md            # Comparación detallada pre/post
│   └── setup-guide.md           # Guía paso a paso
├── oribio/
│   ├── squad.config.ts          # Config tipada para Oribio
│   ├── .squad/
│   │   ├── team.md              # Equipo Oribio
│   │   ├── routing.md           # Routing rules
│   │   ├── decisions.md         # Decisiones iniciales
│   │   └── agents/              # Charters de agentes
│   └── upstream.json            # Herencia para repos hijos
└── personal/
    ├── squad.config.ts          # Config personal Microsoft
    └── .squad/
        ├── team.md              # Equipo personal
        ├── routing.md           # Routing rules
        └── decisions.md         # Decisiones personales
```

## Quick Start

```bash
# Instalar Squad CLI
npm install -g @bradygaster/squad-cli

# Para Oribio (en cualquier repo de Oribio-Co)
squad init
squad upstream add https://github.com/aldogomezmsft/squad-setup.git --name oribio-base --ref main

# Para proyectos personales
squad init --global
```

## Links

- [Squad Docs](https://bradygaster.github.io/squad/)
- [GitHub repo](https://github.com/bradygaster/squad)
- [Oribio MCP Server](https://github.com/Oribio-Co/Oribio-MCP-Server)
- [Oribio Brain Setup](https://github.com/Oribio-Co/Oribio-Brain-Setup)
