# Planes de integracion de la memoria desde especificaciones

## Proposito

Este indice organiza la integracion de la memoria tecnica PCI a partir de los archivos de `Proyecto/Especificaciones/`, usando como base documental `Proyecto/Anotaciones/`, `Proyecto/resultados_calculos.md`, los anexos de `Practica_PCI_LaTeX/` y la estructura real de `Practica_PCI_LaTeX/main.tex`.

El objetivo no es redefinir la plantilla LaTeX, sino conducir cada especificacion hacia su bloque ya existente en la memoria:

- `Resumen`
- `Introduccion e objetivos`
- `Metodologia`
- `Datos introducidos en el programa`
- `Topologia del edificio y seleccion del esquema de instalacion`
- `Justificacion del trazado elegido`
- `Equipos instalados y materiales de la instalacion`
- `Resultados y discusion`
- `Analisis de la verificacion hidraulica mediante mapa de estados`
- `Analisis de los puntos singulares mas desfavorables`
- `Conclusiones`

## Agentes enlazados

- Orquestacion: [task-orchestrator](../../.agents/agents/task-orchestrator.md)
- Investigacion tecnica: [pci-researcher](../../.agents/agents/pci-researcher.md)
- Consolidacion editorial LaTeX: [latex-writer](../../.agents/agents/latex-writer.md)
- Validacion LaTeX: [latex-validator](../../.agents/agents/latex-validator.md)

## Activacion secuencial

- [Plan maestro de activacion secuencial](plan_activacion_secuencial_integracion_memoria.md): ordena el cierre de los cinco Markdown modulares antes de una consolidacion LaTeX global final.
- El plan maestro incluye una fase de cierre normativo: revisar enlaces web en `Proyecto/Anotaciones/`, consultar NotebookLM `PCI_Practica`/`PCI_Practicas` mediante `nlm-skill` y convertir normativa, manuales, catalogos y fichas tecnicas a referencias IEEE sin fechas de acceso ni URLs.

## Planes por especificacion

| Especificacion | Plan de integracion | Bloque principal en memoria |
| --- | --- | --- |
| [00_resumen.md](../Especificaciones/00_resumen.md) | [plan_integracion_00_resumen.md](plan_integracion_00_resumen.md) | `Resumen` |
| [01_introduccion_objetivos.md](../Especificaciones/01_introduccion_objetivos.md) | [plan_integracion_01_introduccion_objetivos.md](plan_integracion_01_introduccion_objetivos.md) | `Introduccion e objetivos` |
| [02_metodologia.md](../Especificaciones/02_metodologia.md) | [plan_integracion_02_metodologia.md](plan_integracion_02_metodologia.md) | `Metodologia` y subsecciones |
| [03_resultados_discusion.md](../Especificaciones/03_resultados_discusion.md) | [plan_integracion_03_resultados_discusion.md](plan_integracion_03_resultados_discusion.md) | `Resultados y discusion` y subsecciones |
| [04_conclusiones.md](../Especificaciones/04_conclusiones.md) | [plan_integracion_04_conclusiones.md](plan_integracion_04_conclusiones.md) | `Conclusiones` |

## Flujo comun recomendado

1. Abrir la tarea con `task-orchestrator`, indicando el archivo de especificacion, el bloque LaTeX destino y las fuentes de anotaciones.
2. Pedir a `pci-researcher` un reporte de trazabilidad tecnica antes de redactar o consolidar.
3. Confirmar que el Markdown de la especificacion queda cerrado y no contiene datos pendientes.
4. Invocar a `latex-writer` solo para transformar el contenido cerrado en fragmento o cambio dentro de `Practica_PCI_LaTeX/main.tex`.
5. Invocar a `latex-validator` despues de la insercion LaTeX para revisar alcance, estatica y compilacion cuando exista contexto compilable.

## Bloqueos transversales

- No existen `Proyecto/Alcance.md`, `Proyecto/Datos.md`, `Proyecto/Planificacion/esquema_memoria.md` ni `Proyecto/Planificacion/mapeo_markdown_a_latex.md`; cada plan declara este vacio como condicion de control.
- Algunos valores de `Proyecto/resultados_calculos.md` deben contrastarse con el informe final de auditoria antes de cerrar la memoria, porque el documento de calculo contiene historicos y tablas extensas.
- La salida primaria sigue siendo Markdown en `Proyecto/Especificaciones/`; `Practica_PCI_LaTeX/` es la capa posterior de consolidacion editorial.
- La plantilla LaTeX ya tiene la estructura destino. No se debe reestructurar `Practica_PCI_LaTeX/main.tex` salvo orden explicita.
