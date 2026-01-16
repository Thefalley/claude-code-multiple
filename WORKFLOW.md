# Workflow de Colaboración Multi-Terminal

## Objetivo
Este repositorio permite trabajar con 4 instancias de Claude Code simultáneamente, coordinando tareas entre ellas.

## Estructura del Proyecto

```
claude-code-multiple/
├── terminal1/          # Backend/API
├── terminal2/          # Frontend
├── terminal3/          # Tests
├── terminal4/          # Documentación/DevOps
├── TASKS_TERMINAL_1.md # Tareas para Terminal 1
├── TASKS_TERMINAL_2.md # Tareas para Terminal 2
├── TASKS_TERMINAL_3.md # Tareas para Terminal 3
├── TASKS_TERMINAL_4.md # Tareas para Terminal 4
├── WORKFLOW.md         # Este archivo
└── README.md           # Documentación principal
```

## Flujo de Trabajo

### 1. Inicio de Sesión (Cada Terminal)
```bash
cd /ruta/al/repositorio/claude-code-multiple
claude-code
```

### 2. Antes de Empezar a Trabajar
Cada instancia de Claude debe:
1. Leer su archivo de tareas: `TASKS_TERMINAL_X.md`
2. Hacer pull del repositorio: `git pull origin main`
3. Revisar cambios recientes de otros terminales

### 3. Durante el Trabajo
- Trabajar SOLO en tu directorio asignado (`terminalX/`)
- Mantener comunicación mediante commits descriptivos
- Actualizar tu archivo de tareas cuando completes algo
- Hacer commits frecuentes con mensajes claros

### 4. Al Terminar una Tarea
```bash
git add .
git commit -m "Terminal X: descripción de lo realizado"
git pull origin main --rebase  # Resolver conflictos si hay
git push origin main
```

### 5. Resolución de Conflictos
Si hay conflictos:
1. Resolver manualmente
2. Marcar como resuelto: `git add <archivo>`
3. Continuar: `git rebase --continue`
4. Hacer push: `git push origin main`

## Responsabilidades por Terminal

### Terminal 1 - Backend/API
- Desarrollo de APIs REST
- Lógica de negocio
- Integración con bases de datos
- Directorio: `terminal1/`

### Terminal 2 - Frontend
- Interfaces de usuario
- Componentes visuales
- Integración con APIs
- Directorio: `terminal2/`

### Terminal 3 - Tests
- Tests unitarios
- Tests de integración
- Tests end-to-end
- Directorio: `terminal3/`

### Terminal 4 - Documentación/DevOps
- Documentación técnica
- CI/CD pipelines
- Scripts de automatización
- Directorio: `terminal4/`

## Comandos Útiles

```bash
# Ver estado del repositorio
git status

# Ver historial de commits
git log --oneline -10

# Ver quién está trabajando en qué
git log --since="1 hour ago" --oneline

# Descartar cambios locales (CUIDADO)
git reset --hard origin/main
```

## Reglas de Oro

1. **SIEMPRE** hacer pull antes de empezar a trabajar
2. **NUNCA** trabajar fuera de tu directorio asignado sin coordinación
3. **SIEMPRE** hacer commits con mensajes descriptivos
4. **SIEMPRE** hacer push después de completar una tarea
5. Comunicar en los commits si necesitas algo de otro terminal

## Ejemplo de Commit Messages

```
Terminal 1: Añadido endpoint POST /api/users
Terminal 2: Implementado formulario de registro
Terminal 3: Agregados tests para endpoint /api/users
Terminal 4: Actualizada documentación de API
```
