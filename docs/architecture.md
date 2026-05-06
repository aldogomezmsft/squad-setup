# Arquitectura Squad — Oribio + Personal

## Visión General

```
┌──────────────────────────────────────────────────────────────────┐
│                         UPSTREAM HIERARCHY                         │
├──────────────────────────────────────────────────────────────────┤
│                                                                    │
│   aldogomezmsft/squad-setup (este repo)                           │
│   ├── oribio/  ─────────────────┐                                 │
│   │   Base config para Oribio   │                                 │
│   │                             ▼                                 │
│   │                    Oribio-Co repos                             │
│   │                    ├── Oribio_SuperApp                         │
│   │                    ├── Oribio-MCP-Server                       │
│   │                    ├── Oribio_Landing_Page                     │
│   │                    └── (futuros repos)                         │
│   │                                                               │
│   └── personal/ ────────────────┐                                 │
│       Squad global personal     │                                 │
│                                 ▼                                 │
│                        aldogomezmsft repos                         │
│                        └── (proyectos Microsoft)                   │
│                                                                    │
└──────────────────────────────────────────────────────────────────┘
```

## Flujo de datos

```
                    ┌─────────────┐
                    │  Usuario    │
                    │  (Aldo)     │
                    └──────┬──────┘
                           │ "Team, build X"
                           ▼
                    ┌─────────────┐
                    │ Coordinator │ ← Lee .squad/decisions.md
                    │  (Squad)    │ ← Lee .squad/routing.md
                    └──────┬──────┘
                           │ Descompone + asigna
                    ┌──────┼──────────────┐
                    ▼      ▼              ▼
              ┌─────────┐ ┌─────────┐ ┌─────────┐
              │ Agent A │ │ Agent B │ │ Agent C │
              │(Backend)│ │(Frontend│ │(Tester) │
              └────┬────┘ └────┬────┘ └────┬────┘
                   │           │           │
                   ▼           ▼           ▼
              Código +     Código +     Tests +
              decisiones   decisiones   decisiones
                   │           │           │
                   └───────────┼───────────┘
                               ▼
                    ┌─────────────────┐
                    │     Scribe      │ ← Persiste decisiones
                    │  (silencioso)   │ ← Actualiza memorias
                    └─────────────────┘
```

## Integración con stack actual

### Oribio

| Componente | Rol | Interacción con Squad |
|------------|-----|-----------------------|
| `Oribio-MCP-Server` | Base de conocimiento | Los agentes consultan vía MCP para datos del negocio |
| `copilot-instructions.md` | System prompt base | Se mantiene — Squad lo complementa, no reemplaza |
| `Oribio_Security` | Políticas | Se refleja en `.squad/decisions.md` como directivas |

### Personal (Microsoft)

| Componente | Rol | Interacción con Squad |
|------------|-----|-----------------------|
| Global instructions | Preferencias de código | Se heredan como decisions en Squad |
| Repos de trabajo | Proyectos activos | Cada uno hereda del upstream personal |

## Modelo de herencia

```
squad-setup/oribio/.squad/        (upstream base)
         │
         ├── decisions.md          → Heredado por todos los repos Oribio
         ├── routing.md            → Routing por defecto
         ├── skills/               → Skills compartidos
         └── agents/               → Charters base
                │
                ▼ (override en repo hijo)
Oribio_SuperApp/.squad/
         ├── decisions.md          → Decisiones locales + heredadas
         ├── routing.md            → Override routing si necesario
         └── agents/               → Agentes específicos del proyecto
```
