---
tags: [system/skill, system/generator, system/trigger, system/projects]
---
# Skill: Project Generator

## 🔔 Triggers
- "Nuevo proyecto..."
- "Crear proyecto..."
- "Genera proyecto sistematizado..."
- "Setup proyecto..."
- "Inicializar proyecto..."

---

## 🧩 Protocolo de Generación (3 Fases)

> [!TIP]
> Ejecuta fase por fase, esperando la respuesta del usuario antes de continuar.

---

### FASE 1 — Identidad y Alcance
Preguntar al usuario:
1. **Nombre del Proyecto**: ¿Cómo se llamará la carpeta? *(Ej: Lanzamiento_Web, Remodelacion_Casa, Curso_Python)*
2. **Propósito / Entregable ("The Shipped")**: ¿Qué significa exactamente que este proyecto está terminado? *(Criterio de éxito concreto)*
3. **Fecha Límite Estimada**: ¿Para cuándo debe estar completado?
4. **Tipo de Proyecto**: ¿Es de trabajo / cliente, personal, formativo o creativo?

---

### FASE 2 — Componentes Deseados
Preguntar si desea incluir:
- [x] **📊 Tablero Kanban**: Para gestionar tareas (`Backlog`, `To Do`, `In Progress`, `Done`).
- [x] **📥 Inbox Local**: Para notas rápidas exclusivas de este proyecto (`01_Inbox/📥_Quick_Capture_[Nombre].md`).
- [x] **📄 Contexto de Proyecto**: Documento con objetivos, enlaces y decisiones clave.
- [ ] **Carpetas Adicionales**: ¿Deseas subcarpetas como `reuniones/`, `documentos/`, `pruebas/` o `recursos/`?

---

### FASE 3 — Generación Automática
Tras la confirmación:
1. Crear la estructura en `10_PROJECTS/[Nombre_Proyecto]/`:
   ```
   10_PROJECTS/[Nombre_Proyecto]/
   ├── context_[Nombre_Proyecto].md
   ├── 📊_Tablero_Kanban.md
   ├── 01_Inbox/
   │   └── 📥_Quick_Capture_[Nombre_Proyecto].md
   └── [subcarpetas seleccionadas]
   ```
2. **Registrar en la Lista Maestra**:
   - Agregar el proyecto en `00_SYSTEM/Dashboards/📋_Lista_Maestra_Pendientes.md` bajo `## 🟡 Proyectos Activos (Prioridad Alta)`.
3. **Confirmar al usuario**:
   - Mostrar enlaces directos al tablero y al contexto creado.
