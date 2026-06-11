# Plan: Crear investigador PCI sustituyendo `solar-termica-researcher`

## Resumen
Sustituir el subagente solar por un subagente de investigación técnica de protección contra incendios con nombre adaptado al proyecto, por ejemplo `.agents/agents/pci-researcher.md`. El nuevo agente conservará el mismo estilo operativo del agente actual: frontmatter YAML, permisos restrictivos, fuentes canónicas ordenadas, alcance estricto, flujo de trabajo, formato de salida y criterios de calidad.

La nueva versión debe estar orientada a la documentación PCI disponible en el proyecto, con especial peso de `Manuales_PCI` y `PCI_Practicas`, y alineada con la estructura de la memoria PCI existente.

## Cambios clave
- Crear o renombrar el agente con un nombre propio del dominio PCI, recomendado: `.agents/agents/pci-researcher.md`.
- Actualizar `.agents/agents/task-orchestrator.md` para que permita e invoque el nuevo agente PCI en lugar de `solar-termica-researcher`.
- Eliminar las referencias operativas al nombre solar dentro del flujo de agentes.
- Reescribir la identidad del agente de solar térmica a PCI, sin cambiar su estilo de redacción ni su estructura general.
- Sustituir las fuentes canónicas por una jerarquía PCI:
  - `Proyecto/Alcance.md`, `Proyecto/Datos.md` y documentación de planificación, si existe.
  - NotebookLM: `Manuales_PCI` y `PCI_Practicas`.
  - `Proyecto/Anotaciones/`.
  - `Proyecto/Especificaciones/`.
  - `00_Data/`.
  - `Normativa/`.
  - `00_Instalacion/`.
  - `Practica_PCI_LaTeX/`.
- Adaptar el alcance técnico a:
  - BIEs.
  - rociadores automáticos.
  - red hidráulica PCI.
  - abastecimiento, cálculo de caudales y presiones.
  - sectorización, evacuación y criterios normativos cuando proceda.
- Conservar el formato de salida basado en trazabilidad:
  - marco canónico,
  - evidencias por fuente,
  - criterios normativos,
  - cálculos o criterios de selección,
  - artefactos reutilizables,
  - vacíos o bloqueos,
  - recomendación para redacción.

## Implementación prevista
1. Usar `.agents/agents/solar-termica-researcher.md` como plantilla estructural.
2. Crear el nuevo agente con nombre PCI, recomendado: `.agents/agents/pci-researcher.md`.
3. Reescribir el frontmatter con descripción y propósito PCI, manteniendo `mode: subagent` y `permission.edit: deny`.
4. Cambiar el cuerpo del agente para que el dominio, el alcance y los límites sean PCI.
5. Integrar `Manuales_PCI` y `PCI_Practicas` como fuentes canónicas de trabajo futuras.
6. Actualizar `task-orchestrator` para reemplazar permisos, menciones e invocaciones de `solar-termica-researcher` por `pci-researcher`.
7. Ajustar la salida esperada a la estructura de memoria PCI del proyecto y a las secciones reales de `Practica_PCI_LaTeX/main.tex`.
8. Mantener la obligación de declarar huecos, contradicciones y datos pendientes sin inventar normativa ni resultados.
9. Retirar o archivar el agente solar anterior si ya no tiene uso en este proyecto.

## Plan de verificación
- Validación estática del Markdown:
  - YAML correcto.
  - No quedan referencias residuales a solar térmica, captadores, acumulación o respaldo de gas natural.
  - El nombre del agente, título interno y descripción son propios de PCI.
  - El tono y el contrato operativo siguen el patrón del agente original.
- Validación de integración:
  - El orquestador invoca el nuevo subagente PCI por su nuevo identificador.
  - No quedan permisos ni referencias activas a `solar-termica-researcher`.
  - El nuevo texto sigue siendo consumible por los agentes posteriores del flujo documental.
- Validación de trazabilidad:
  - El plan deja explícitas las fuentes locales y NotebookLM que deberán consultarse en la implementación real.

## Supuestos
- El nombre del agente debe adaptarse al proyecto PCI; se recomienda `pci-researcher`.
- El agente solar anterior no debe quedar como nombre operativo principal del proyecto.
- Los notebooks `Manuales_PCI` y `PCI_Practicas` se reservarán para la fase de implementación o uso futuro del agente.
- El estilo del agente debe seguir siendo técnico, estricto y trazable, no narrativo ni divulgativo.
