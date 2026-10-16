---
cssclasses:
  - dashboard
  - workplace-dashboard
---

# 🏢 Mi Centro de Control (Workplace)

> [!rocket] ⚡ Accesos Rápidos
> - [[01_INBOX/📥_Quick_Capture|📥 Quick Capture]]
> - [[00_SYSTEM/Dashboards/📋_Lista_Maestra_Pendientes|📋 Lista Maestra de Pendientes]]
> - [[00_SYSTEM/Context/OS_Context|🧠 Mi Perfil (OS Context)]]
> - [[00_SYSTEM/Agents/AGENTS|🤖 Configuración de Agentes]]
> - [[START_HERE|🚀 Guía de Inicio]]

---

> [!todo] ✅ Pendientes Próximos (Citas y Fechas Clave)
> ```dataviewjs
> const master = dv.page("00_SYSTEM/Dashboards/📋_Lista_Maestra_Pendientes.md");
> if (master && master.file) {
>   const re = /(\d{4}-\d{2}-\d{2})/;
>   const dated = [];
>   for (const t of master.file.tasks.where(t => !t.completed)) {
>     const m = t.text.match(re);
>     if (m) dated.push([m[1], t]);
>   }
>   dated.sort((a, b) => a[0].localeCompare(b[0]));
>   if (dated.length > 0) {
>     dv.taskList(dated.map(p => p[1]), false);
>   } else {
>     dv.paragraph("✨ *No hay tareas con fecha próxima pendientes.*");
>   }
> } else {
>   dv.paragraph("ℹ️ Abre [[00_SYSTEM/Dashboards/📋_Lista_Maestra_Pendientes]] para ver todas tus tareas.");
> }
> ```
> 
> → [[00_SYSTEM/Dashboards/📋_Lista_Maestra_Pendientes|📋 Ver Todos los Pendientes]]

---

> [!folder] 🚀 Proyectos Activos (`10_PROJECTS/`)
> ```dataview
> TABLE file.folder as Carpeta, file.mtime as "Última Modificación"
> FROM "10_PROJECTS"
> WHERE file.name != "README" AND file.folder != "10_PROJECTS"
> SORT file.mtime desc
> LIMIT 10
> ```

---

> [!leaf] 🌱 Áreas de Vida (`20_AREAS/`)
> - [[20_AREAS/Salud_Bienestar/🏥_Salud_Personal|🏥 Salud & Bienestar]]
> - [[20_AREAS/Finanzas/💰_Control_Financiero|💰 Finanzas Personales]]
> - [[20_AREAS/Crecimiento_Profesional/🚀_Metas_y_Habilidades|🚀 Carrera & Habilidades]]
