---
tags: [system/skill, system/meta, system/trigger]
---
# Skill: Meta Skill Generator (Creador de Habilidades)

## 🔔 Triggers
- "Crea una nueva skill para..."
- "Enséñale una nueva habilidad a la IA..."
- "Quiero un nuevo comando para..."
- "Genera una skill de..."

---

## 🎯 Propósito
Permitir que el usuario o el Agente de Onboarding creen nuevas skills modulares y consistentes en `00_SYSTEM/Skills/` siguiendo la arquitectura del Segundo Cerebro.

---

## 📋 Protocolo de Creación

1. **Definir el Alcance con el Usuario**:
   - **Nombre de la Skill**: `[Nombre]_Skill.md`
   - **Triggers**: Frases comunes que dispararán la skill.
   - **Archivo Destino**: ¿A qué nota, área o carpeta afectará?
   - **Acción requerida**: ¿Crear nota, actualizar lista, formatear texto, calcular algo?
   - **Plantilla asociada**: ¿Requiere una plantilla en `00_SYSTEM/Templates/`?

2. **Generar el Archivo**:
   - Crear `00_SYSTEM/Skills/[Nombre]_Skill.md` utilizando el estándar definido en [[00_SYSTEM/Agents/SYSTEM_BUILDER]].

3. **Registrar la Skill**:
   - Añadir la nueva fila a la tabla de Skills en [[00_SYSTEM/Agents/AGENTS]] y [[00_SYSTEM/Agents/CLAUDE]].
   - Añadir la regla de clasificación a [[00_SYSTEM/Skills/Inbox_Capture_Skill]] si aplica.

4. **Confirmar**:
   - Informar al usuario que la nueva habilidad está activa y lista para ser probada.
