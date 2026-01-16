# Claude Code Multiple - Colaboración Multi-Terminal

## Descripción
Proyecto experimental para trabajar con 4 instancias de Claude Code simultáneamente en un mismo repositorio de GitHub, permitiendo colaboración coordinada entre múltiples agentes de IA.

## Concepto
Este repositorio está diseñado para ser trabajado por 4 instancias diferentes de Claude Code, cada una con responsabilidades específicas:

- **Terminal 1**: Backend/API
- **Terminal 2**: Frontend
- **Terminal 3**: Testing
- **Terminal 4**: Documentación/DevOps

## Estructura del Proyecto

```
claude-code-multiple/
├── terminal1/              # Código de Backend/API
├── terminal2/              # Código de Frontend
├── terminal3/              # Tests y cobertura
├── terminal4/              # Documentación y scripts DevOps
├── TASKS_TERMINAL_1.md     # Tareas asignadas a Terminal 1
├── TASKS_TERMINAL_2.md     # Tareas asignadas a Terminal 2
├── TASKS_TERMINAL_3.md     # Tareas asignadas a Terminal 3
├── TASKS_TERMINAL_4.md     # Tareas asignadas a Terminal 4
├── WORKFLOW.md             # Guía de flujo de trabajo
└── README.md               # Este archivo
```

## Cómo Usar

### Requisitos Previos
- Git instalado
- Claude Code instalado
- Acceso al repositorio (SSH configurado)

### Paso 1: Clonar el Repositorio (Una Sola Vez)
```bash
git clone git@github.com:Thefalley/claude-code-multiple.git
cd claude-code-multiple
```

### Paso 2: Abrir 4 Terminales
Abre 4 ventanas de terminal en tu sistema operativo y navega al directorio del proyecto en cada una:
```bash
cd /ruta/al/proyecto/claude-code-multiple
```

### Paso 3: Iniciar Claude Code en Cada Terminal
En cada una de las 4 terminales, ejecuta:
```bash
claude-code
```

### Paso 4: Asignar Tareas
Como coordinador, edita los archivos `TASKS_TERMINAL_X.md` para asignar tareas específicas a cada terminal.

Por ejemplo, en `TASKS_TERMINAL_1.md`:
```markdown
## Tareas Pendientes
- [ ] Crear API REST con Express.js
- [ ] Implementar endpoint GET /api/users
- [ ] Implementar endpoint POST /api/users
```

### Paso 5: Monitorear y Coordinar
Cada instancia de Claude Code:
1. Leerá su archivo de tareas
2. Hará pull para obtener cambios recientes
3. Trabajará en su directorio asignado
4. Hará commit y push al completar tareas

## Flujo de Trabajo para Cada Terminal

### Al Iniciar
```bash
# Cada Claude debe hacer esto primero
git pull origin main

# Leer su archivo de tareas
# Por ejemplo, Terminal 1 lee: TASKS_TERMINAL_1.md
```

### Durante el Trabajo
- Trabajar SOLO en el directorio asignado (`terminal1/`, `terminal2/`, etc.)
- Hacer commits frecuentes con mensajes descriptivos
- Formato de commit: `Terminal X: descripción clara de lo realizado`

### Al Completar una Tarea
```bash
git add .
git commit -m "Terminal 1: Implementado endpoint POST /api/users"
git pull origin main --rebase
git push origin main
```

## Ventajas de Este Sistema

1. **Especialización**: Cada terminal se enfoca en un área específica
2. **Paralelización**: 4 agentes trabajando simultáneamente
3. **Coordinación**: Sistema de tareas y commits para mantenerse sincronizados
4. **Trazabilidad**: Historial claro de quién hizo qué

## Consejos para el Coordinador (Tú)

1. **Asigna tareas claras y específicas** en los archivos `TASKS_TERMINAL_X.md`
2. **Monitorea el progreso** con `git log --oneline -10`
3. **Resuelve conflictos** si dos terminales editan el mismo archivo
4. **Reasigna tareas** si un terminal se queda sin trabajo
5. **Revisa commits** regularmente para verificar el progreso

## Comandos Útiles para Monitoreo

```bash
# Ver últimos 10 commits
git log --oneline -10

# Ver actividad reciente (última hora)
git log --since="1 hour ago" --oneline

# Ver estado actual
git status

# Ver diferencias
git diff
```

## Resolución de Problemas

### Si un Terminal se Queda Atascado
1. Edita su archivo `TASKS_TERMINAL_X.md`
2. Agrega una nueva tarea clara
3. La instancia de Claude lo leerá y continuará

### Si Hay Conflictos de Git
1. Claude intentará resolver automáticamente
2. Si no puede, revisa manualmente con `git status`
3. Resuelve el conflicto y haz `git add` + `git rebase --continue`

### Si Quieres Reiniciar un Terminal
```bash
# En ese terminal específico
git reset --hard origin/main
git pull origin main
```

## Ejemplo de Sesión Completa

1. **Coordinador** edita `TASKS_TERMINAL_1.md` con: "Crear servidor Express básico"
2. **Terminal 1** lee el archivo, crea el servidor en `terminal1/server.js`
3. **Terminal 1** hace commit: `Terminal 1: Creado servidor Express básico`
4. **Coordinador** edita `TASKS_TERMINAL_2.md` con: "Crear componente React que llame al servidor"
5. **Terminal 2** hace pull, ve el código de Terminal 1, crea el componente
6. **Terminal 2** hace commit: `Terminal 2: Creado componente de ejemplo`
7. **Coordinador** edita `TASKS_TERMINAL_3.md` con: "Crear tests para el servidor"
8. **Terminal 3** hace pull, crea tests, hace commit
9. **Coordinador** edita `TASKS_TERMINAL_4.md` con: "Documentar la API"
10. **Terminal 4** hace pull, crea documentación, hace commit

## Licencia
MIT

## Autor
Thefalley (pabmenegi@gmail.com)

## Notas
Este es un proyecto experimental para explorar la colaboración entre múltiples instancias de IA trabajando en el mismo codebase.
