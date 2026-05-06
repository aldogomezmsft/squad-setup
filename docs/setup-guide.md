# Guía de Setup — Squad para Oribio y Personal

## Prerrequisitos

- Node.js 18+
- npm
- GitHub Copilot (CLI o VS Code)
- Git

## 1. Instalar Squad CLI

```bash
npm install -g @bradygaster/squad-cli
squad --version
```

## 2. Setup para Oribio-Co

### 2.1 Inicializar en un repo existente

```bash
cd Oribio_SuperApp  # o cualquier repo de Oribio-Co
squad init
```

### 2.2 Conectar upstream (herencia org)

```bash
squad upstream add https://github.com/aldogomezmsft/squad-setup.git --name oribio-org --ref main
squad upstream sync oribio-org
```

Esto hereda:
- Decisiones organizacionales (seguridad, estándares)
- Routing rules por defecto
- Skills compartidos

### 2.3 Verificar

```bash
squad upstream list
squad status
```

## 3. Setup Personal (Global)

### 3.1 Inicializar squad global

```bash
squad init --global
```

Esto crea tu squad personal en:
- **Windows:** `%APPDATA%\squad\`
- **macOS:** `~/Library/Application Support/squad/`
- **Linux:** `~/.config/squad/`

### 3.2 Conectar upstream personal

```bash
squad upstream add https://github.com/aldogomezmsft/squad-setup.git --name personal-base --ref main
```

## 4. Uso diario

### Abrir sesión con Squad

```bash
# En CLI
copilot --agent squad

# O simplemente
squad
```

### Comandos útiles

| Comando | Función |
|---------|---------|
| `squad status` | Ver estado del equipo |
| `squad watch` | Modo watch (actualización continua) |
| `squad export` | Exportar equipo (snapshot) |
| `squad upstream sync` | Sincronizar upstreams |

### Patrones de trabajo

```bash
# Tarea para un agente específico
> "Dallas, refactoriza el endpoint de productos"

# Fan-out paralelo (usar "team")
> "Team, implementen la feature de carrito abandonado"

# Establecer directiva
> "Siempre usar TypeScript strict mode"

# Ver decisiones acumuladas
> "Muéstrame las decisiones"
```

## 5. Mantener sincronizado

### Cuando se actualice este repo (squad-setup)

Desde cualquier repo hijo:
```bash
squad upstream sync oribio-org
```

### Cuando se tomen nuevas decisiones

Las decisiones se acumulan automáticamente en `.squad/decisions.md`. Commitear después de sesiones productivas:

```bash
git add .squad/
git commit -m "squad: persist team decisions from session"
```

## 6. Troubleshooting

### Squad no encuentra `.squad/`
```bash
squad init  # en el repo
```

### Upstream no sincroniza
```bash
squad upstream list         # verificar config
squad upstream remove nombre
squad upstream add <url> --name nombre
squad upstream sync nombre
```

### Agentes no ven contexto heredado
Reiniciar sesión — la resolución de upstreams ocurre al inicio de sesión.
