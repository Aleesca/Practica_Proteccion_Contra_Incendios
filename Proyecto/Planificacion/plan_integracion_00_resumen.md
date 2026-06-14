# Plan de integracion: `00_resumen.md`

## Tarea objetivo

- Especificacion fuente: [00_resumen.md](../Especificaciones/00_resumen.md)
- Seccion destino: `Resumen`
- Salida primaria: Markdown cerrado en `Proyecto/Especificaciones/00_resumen.md`
- Salida posterior: fragmento LaTeX en `Practica_PCI_LaTeX/main.tex`, dentro de `\section*{Resumen}`
- Agentes: [task-orchestrator](../../.agents/agents/task-orchestrator.md), [pci-researcher](../../.agents/agents/pci-researcher.md), [latex-writer](../../.agents/agents/latex-writer.md), [latex-validator](../../.agents/agents/latex-validator.md)

## Fuentes canonicas

- [Resultados de calculo](../resultados_calculos.md)
- [Revision normativa y resultados de calculos](../Anotaciones/informe_revision_normativa_resultados_calculos.md)
- Anexo de calculos: `../../Practica_PCI_LaTeX/Figuras/Anejo_calculo.pdf`
- Planos: `../../Practica_PCI_LaTeX/Figuras/Planos/`
- Plantilla: `../../Practica_PCI_LaTeX/main.tex`

## Objetivo de integracion

Convertir la propuesta de resumen en un texto ejecutivo de no mas de 250 palabras que presente alcance, metodologia, resultados principales y conclusion tecnica sin listas, referencias, ecuaciones ni abreviaciones.

El resumen debe anticipar estos datos finales:

- Grupo de presion: 10,53 L/s y 99,63 mca.
- Bocas de Incendio Equipadas simultaneas: nudos 122 y 125.
- Caudal total de Bocas de Incendio Equipadas: 200,91 L/min.
- Rociadores activos: nudos 140, 141 y 142.
- Caudal total de rociadores: 430,87 L/min.
- Reserva total estimada: 37.906,87 L.
- Punto critico de Boca de Incendio Equipada: nudo 125, con 2,000 bar en boquilla.
- Punto critico de rociador: nudo 142, con 2,829 bar.

## Secuencia de agentes

### 1. `task-orchestrator`

```yaml
agente: task-orchestrator
tarea: Integrar la especificacion 00_resumen.md en la seccion Resumen.
entradas:
  - Proyecto/Especificaciones/00_resumen.md
  - Proyecto/resultados_calculos.md
  - Proyecto/Anotaciones/informe_revision_normativa_resultados_calculos.md
  - Practica_PCI_LaTeX/main.tex
salida_esperada: Markdown cerrado y listo para consolidacion editorial.
control: No reestructurar main.tex y no anadir referencias dentro del resumen.
```

### 2. `pci-researcher`

```yaml
agente: pci-researcher
seccion: Resumen
proposito: Confirmar la trazabilidad de los valores numericos finales que se van a mencionar.
pedir:
  - Verificacion de grupo de presion, caudales, reserva y puntos criticos.
  - Identificacion de discrepancias entre resultados_calculos.md y el informe final de auditoria.
  - Lista de datos que no deben entrar por ser demasiado detallados para el resumen.
```

### 3. `latex-writer`

```yaml
agente: latex-writer
seccion: Resumen
fuente_markdown: Proyecto/Especificaciones/00_resumen.md
accion: Convertir el texto final en fragmento LaTeX e insertarlo en la seccion existente si se solicita consolidacion.
restricciones:
  - Sin listas.
  - Sin tablas.
  - Sin citas bibliograficas.
  - Sin abreviaturas como BIEs.
```

### 4. `latex-validator`

```yaml
agente: latex-validator
artefacto: Practica_PCI_LaTeX/main.tex
accion: Validar que el resumen compila y respeta la convencion editorial.
checks:
  - Texto dentro de \section*{Resumen}.
  - Sin figuras, tablas, ecuaciones ni referencias.
  - Extension maxima de 250 palabras.
```

## Fases de ejecucion

### Fase 1. Cierre de datos

- Comparar los valores de `00_resumen.md` con `informe_revision_normativa_resultados_calculos.md`.
- Revisar si el PDF de calculos y `resultados_calculos.md` mantienen valores historicos distintos.
- Elegir como fuente de cierre el informe final de auditoria salvo que el usuario indique otra version.

### Fase 2. Ajuste del texto ejecutivo

- Mantener tres parrafos como maximo.
- Sustituir cualquier abreviatura por la denominacion completa.
- Eliminar referencias a anexos concretos si rompen la regla de resumen sin referencias.

### Fase 3. Consolidacion LaTeX

- Insertar solo el texto del resumen en el bloque existente.
- No crear nueva seccion ni modificar el indice.
- Mantener el resumen antes de `Introduccion e objetivos`.

### Fase 4. Validacion

- Revisar palabra por palabra el cumplimiento de estilo.
- Compilar `main.tex` solo cuando la consolidacion haya sido aplicada.

## Criterios de aceptacion

- El resumen no supera 250 palabras.
- No contiene abreviaturas, listas, tablas, figuras, ecuaciones ni referencias bibliograficas.
- Los datos coinciden con la version final auditada.
- La memoria sigue usando la estructura actual de `main.tex`.

## Riesgos o huecos

- Puede existir discrepancia entre valores historicos de `resultados_calculos.md` y el informe final de auditoria.
- La decision sobre incluir referencias normativas explicitas queda fuera del resumen salvo orden expresa.

