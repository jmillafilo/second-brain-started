---
tags: [system/builder, system/architecture, system/meta]
---
# 🛠️ System Builder: Motor de Generación de Skills, Prompts y Templates

Este documento describe la especificación y los lineamientos de diseño que utiliza la IA para generar automáticamente archivos dentro del ecosistema del Segundo Cerebro (`brain-started`).

---

## 📐 1. Estándar de una Skill (`00_SYSTEM/Skills/[Nombre]_Skill.md`)

Cada habilidad creada debe seguir esta estructura exacta:

```markdown
---
tags: [system/skill, system/[modulo], system/trigger]
---
# Skill: [Nombre de la Habilidad]

## 🔔 Triggers (Frases de Activación)
- "[Frase 1]..."
- "[Frase 2]..."
- "[Palabra clave]..."

## 🎯 Propósito
Explicación breve (1-2 líneas) de lo que resuelve esta skill.

## 📋 Protocolo de Ejecución (Paso a Paso)
1. **Paso 1 (Lectura/Detección)**: Leer archivo origen o entrada del usuario.
2. **Paso 2 (Procesamiento/Clasificación)**: Aplicar lógica de enrutamiento o transformación.
3. **Paso 3 (Escritura/Destino)**:
   - Archivo destino: `[Ruta_Relativa_Al_Vault]`
   - Formato o plantilla aplicada.
4. **Paso 4 (Confirmación)**: Reportar al usuario de forma clara qué acción se realizó.

## 📝 Formato de Datos Generados
[Bloque con el formato markdown o frontmatter esperado]
```

---

## 📑 2. Estándar de una Plantilla (`00_SYSTEM/Templates/[Nombre].md`)

Toda plantilla debe:
1. Incluir frontmatter YAML con al menos `tags: [system/template, [categoria]]`.
2. Emplear variables legibles o de Obsidian (`{{date}}`, `{{title}}`, etc.).
3. Tener secciones limpias con emojis para rápida identificación visual.
4. Evitar campos innecesarios que añadan fricción al llenado.

---

## 🤖 3. Estándar de Agentes (`AGENTS.md` y `CLAUDE.md`)

El archivo de configuración del agente debe contar con:
1. **Reglas de Inicio**: Lectura obligatoria de `00_SYSTEM/Context/OS_Context.md` y frase de saludo.
2. **Rol y Comportamiento**: Síntesis de la identidad y objetivo del usuario.
3. **Estructura del Vault y Skills**: Tabla que vincula Skill -> Trigger -> Destino.
4. **Reglas de Seguridad**: Archivos excluidos, respeto a `.aiignore` y prohibición de comandos destructivos.
5. **Estilo de Comunicación**: Tono acordado con el usuario.
6. **Flujo de Trabajo Típico**: Rutina diaria de trabajo con el vault.

---

## 🔄 4. Lógica de Enrutamiento del Inbox (`Inbox_Capture_Skill.md`)

Cuando se agreguen nuevas áreas o proyectos, la IA debe registrar la regla de mapeo en `Inbox_Capture_Skill.md` bajo la tabla de clasificación semántica:

| Categoría Detectada | Destino en Vault | Acción |
| :--- | :--- | :--- |
| **Cita Médica / Evento con Fecha** | `00_SYSTEM/Calendar/` + `📋_Lista_Maestra_Pendientes.md` | Crea evento y añade tarea con fecha |
| **Proyecto Específico** | `10_PROJECTS/[Proyecto]/` | Mueve a inbox local o tablero |
| **Área de Responsabilidad** | `20_AREAS/[Area]/` | Mueve o actualiza nota de seguimiento |
| **Recurso / Conocimiento** | `30_RESOURCES/[Categoria]/` | Crea nota con plantilla de recurso |
| **Tarea Personal General** | `00_SYSTEM/Dashboards/📋_Lista_Maestra_Pendientes.md` | Añade `- [ ] [Tarea]` |
| **Duda o Ambigüedad** | Preguntar al usuario | Dejar en `01_INBOX/📥_Quick_Capture.md` |
