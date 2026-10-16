---
tags: [system/skill, system/inbox, system/trigger, system/para]
---
# Skill: Quick Capture / Inbox

## 🔔 Triggers de Captura Rápida
- "Anota esto rápido..."
- "Tengo una idea..."
- "Recuérdame..."
- "Guarda esto en el inbox..."

## 📥 Acción de Captura
Cuando el usuario proporciona un texto rápido, idea, enlace o tarea:
1. Abre `01_INBOX/📥_Quick_Capture.md`.
2. Si la nota contiene únicamente `*(No hay entradas pendientes)*`, reemplázalo.
3. Agrega la nueva entrada bajo `## 📝 Entradas de Hoy` con timestamp si es relevante.
4. Responde confirmando que ha sido capturado con éxito.

---

# Skill: Inbox Organizer (Enrutador Inteligente PARA)

## 🔔 Triggers de Organización
- "Organiza mi inbox"
- "Limpia mi inbox"
- "Procesa mi inbox"
- "Ordena mi bandeja"
- "Clasifica mis notas"

## 🎯 Protocolo de Enrutamiento (Paso a Paso)

1. **Leer la bandeja**: Abrir y leer todo el contenido de `01_INBOX/📥_Quick_Capture.md`. Si no hay entradas pendientes, avisar al usuario amablemente.
2. **Analizar cada entrada**: Clasificar semánticamente cada ítem en una de las siguientes categorías según el método PARA:

| Categoría Detectada | Destino en Vault | Acción Específica |
| :--- | :--- | :--- |
| **📅 Citas Médicas & Eventos con Fecha/Hora** | `00_SYSTEM/Calendar/` y `📋_Lista_Maestra_Pendientes.md` | • Agrega la tarea con fecha en `## 🔴 Citas Próximas & Eventos con Fecha`<br>• Crea archivo de evento `00_SYSTEM/Calendar/YYYY-MM-DD-[Nombre].md` usando plantilla de Full Calendar. |
| **🚀 Proyectos Específicos (`10_PROJECTS`)** | `10_PROJECTS/[Nombre_Proyecto]/` | • Si el proyecto existe: mueve la tarea o nota a su bandeja interna o tablero Kanban.<br>• Si no existe: pregunta al usuario si desea inicializarlo con `Project_Generator_Skill`. |
| **🌱 Áreas de Responsabilidad (`20_AREAS`)** | `20_AREAS/[Area]/` | • Mueve el registro a la nota de área correspondiente (Salud, Finanzas, Familia, etc.). |
| **📚 Recursos y Referencias (`30_RESOURCES`)** | `30_RESOURCES/[Categoria]/` | • Crea o actualiza una nota de recurso/lectura/herramienta con la información o enlace. |
| **✅ Tareas Personales Sueltas** | `00_SYSTEM/Dashboards/📋_Lista_Maestra_Pendientes.md` | • Agrega como `- [ ] [Tarea]` bajo `## 🟢 Tareas Personales & Áreas`. |
| **❓ Sin Categoría Clara** | Preguntar al usuario | • Solicita aclaración o deja la entrada en el inbox indicando el motivo. |

3. **Formato de Eventos de Calendario (Full Calendar)**:
   Si una entrada contiene fecha y hora (ej: *"Dentista 24 de Octubre a las 15:30"*), crea `00_SYSTEM/Calendar/YYYY-MM-DD-[Nombre].md` con este formato:
   ```markdown
   ---
   title: "[Título del evento]"
   date: YYYY-MM-DD
   startTime: "HH:mm"
   endTime: "HH:mm"
   allDay: false
   calendar: "Google Calendar"
   location: "[Lugar o Clínica]"
   type: event
   tags: [calendar/event]
   ---
   # [Título del evento]

   **Date**: YYYY-MM-DD
   **Time**: HH:mm
   **Location**: [Lugar]
   **Calendar**: Google Calendar

   ## Description
   [Detalles del evento]

   ## Notes
   - Creado automáticamente por Inbox Organizer.
   ```

4. **Limpieza del Inbox**:
   Una vez procesadas y movidas las entradas, reescribe `01_INBOX/📥_Quick_Capture.md` dejándolo limpio con la estructura base:
   ```markdown
   ---
   tags: [system/inbox, type/inbox]
   ---
   # 📥 Quick Capture (Inbox)

   > **Regla de Cero Fricción**: Escribe aquí todo lo que cruce por tu mente. La IA procesará, clasificará y moverá esta información a donde corresponda.

   ## 📝 Entradas de Hoy

   *(No hay entradas pendientes)*
   ```

5. **Reporte de Acciones**:
   Presenta un resumen claro con viñetas al usuario indicando qué ítems se movieron y a qué destino.
