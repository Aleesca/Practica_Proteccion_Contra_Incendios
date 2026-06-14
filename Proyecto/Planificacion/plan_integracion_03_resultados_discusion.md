# Plan de integracion: `03_resultados_discusion.md`

## Tarea objetivo

- Especificacion fuente: [03_resultados_discusion.md](../Especificaciones/03_resultados_discusion.md)
- Secciones destino:
  - `Resultados y discusion`
  - `Analisis de la verificacion hidraulica mediante mapa de estados`
  - `Analisis de los puntos singulares mas desfavorables`
- Salida primaria: Markdown cerrado en `Proyecto/Especificaciones/03_resultados_discusion.md`
- Salida posterior: fragmentos LaTeX en `Practica_PCI_LaTeX/main.tex`
- Agentes: [task-orchestrator](../../.agents/agents/task-orchestrator.md), [pci-researcher](../../.agents/agents/pci-researcher.md), [latex-writer](../../.agents/agents/latex-writer.md), [latex-validator](../../.agents/agents/latex-validator.md)

## Fuentes canonicas

- [Resultados de calculo](../resultados_calculos.md)
- [Revision normativa y resultados de calculos](../Anotaciones/informe_revision_normativa_resultados_calculos.md)
- [Comparativa entre riesgo ordinario y ligero](../Anotaciones/comparativa_riesgo_ordinario_vs_ligero.md)
- [Presion minima de rociador en DMELECT](../Anotaciones/presion-minima-rociador-dmelect.md)
- [Justificacion de simultaneidad de BIEs](../Anotaciones/justificacion_simultaneidad_BIEs.md)
- [Informe de revision de calculos BIE](../Anotaciones/informe_revision_calculos_bie.md)
- Plantilla: `../../Practica_PCI_LaTeX/main.tex`

## Objetivo de integracion

Transformar los resultados hidraulicos en una discusion tecnica: que escenario se calcula, que puntos gobiernan, que cumple, que requiere actuacion puntual y por que el diseno se considera valido. Debe evitar limitarse a copiar tablas del anexo.

## Secuencia de agentes

### 1. `task-orchestrator`

```yaml
agente: task-orchestrator
tarea: Integrar 03_resultados_discusion.md en Resultados y discusion.
entradas:
  - Proyecto/Especificaciones/03_resultados_discusion.md
  - Proyecto/resultados_calculos.md
  - Proyecto/Anotaciones/informe_revision_normativa_resultados_calculos.md
  - Proyecto/Anotaciones/comparativa_riesgo_ordinario_vs_ligero.md
  - Proyecto/Anotaciones/presion-minima-rociador-dmelect.md
  - Proyecto/Anotaciones/justificacion_simultaneidad_BIEs.md
  - Practica_PCI_LaTeX/main.tex
salida_esperada: Discusion con mapa de estados, puntos desfavorables y verificacion normativa resumida.
control: Separar siempre Bocas de Incendio Equipadas y rociadores automaticos.
```

### 2. `pci-researcher`

```yaml
agente: pci-researcher
seccion: Resultados y discusion
proposito: Reunir evidencia numerica y normativa para interpretar los resultados.
pedir:
  - Grupo de presion, caudal total y velocidad maxima final.
  - Bocas de Incendio Equipadas activas, nudos, caudales y presiones.
  - Rociadores activos, nudos, caudales y presiones.
  - Reserva de agua por sistema y total.
  - Justificacion de valvula reductora en la Boca de Incendio Equipada 122.
  - Papel de la comparativa RO1/RL como discusion opcional, no como contradiccion.
```

### 3. `latex-writer`

```yaml
agente: latex-writer
seccion: Resultados y discusion
fuente_markdown: Proyecto/Especificaciones/03_resultados_discusion.md
accion: Consolidar texto, tablas resumidas y referencias a anexos dentro de las subsecciones existentes.
restricciones:
  - No copiar las tablas completas de resultados_calculos.md.
  - Usar tablas resumidas para verificacion normativa si aportan claridad.
  - No presentar RO1/RL como decision abierta si la memoria ya adopta una hipotesis.
```

### 4. `latex-validator`

```yaml
agente: latex-validator
artefacto: Practica_PCI_LaTeX/main.tex
accion: Validar coherencia, tablas y compilacion.
checks:
  - Booktabs en tablas.
  - Cifras con unidades coherentes.
  - No mezclar criterios de Bocas de Incendio Equipadas y rociadores.
  - Sin contradicciones entre valores finales.
```

## Fases de ejecucion

### Fase 1. Congelacion de resultados

- Confirmar si los valores finales son los del informe de auditoria: 10,53 L/s, 99,63 mca y 37.906,87 L.
- Revisar discrepancias con `resultados_calculos.md`, que contiene tambien una nota con 10,58 L/s y 103,96 mca.
- Documentar cualquier discrepancia antes de escribir la version final.

### Fase 2. Mapa de estados

- Explicar para que sirve el mapa de estados.
- Incluir caudal total de diseno, velocidad maxima de 8,62 m/s en la linea 123 y aceptacion de geometria sin cambio general de diametros.
- Evitar convertir el apartado en una transcripcion del software.

### Fase 3. Puntos singulares

- Para Bocas de Incendio Equipadas, separar nudos 122 y 125:
  - Nudo 122: 105,451 L/min, 6,300 bar de entrada y 2,441 bar en boquilla.
  - Nudo 125: 95,462 L/min, 5,163 bar de entrada y 2,000 bar en boquilla.
- Para rociadores, separar nudos 140, 141 y 142:
  - Caudales 152,764 L/min, 143,515 L/min y 134,591 L/min.
  - Nudo 142 como rociador mas desfavorable, con 2,829 bar.

### Fase 4. Verificacion normativa y reserva

- Incluir tabla resumida con criterios de simultaneidad, presion minima, caudal, autonomia y reserva.
- Presentar reservas: 12.054,75 L para Bocas de Incendio Equipadas, 25.852,12 L para rociadores y 37.906,87 L total.
- Explicar la valvula reductora en el nudo 122 como medida puntual.

### Fase 5. Discusion critica

- Indicar que la velocidad maxima es elevada pero admisible frente al limite de 10 m/s.
- Indicar que el aljibe es exigente para un edificio residencial, pero coherente con la hipotesis de calculo.
- Si se menciona RO1/RL, hacerlo como reflexion tecnica o decision de diseno, no como cambio pendiente de la memoria.

### Fase 6. Validacion

- Validar unidades, decimales y consistencia de cifras.
- Compilar solo despues de la insercion LaTeX.

## Criterios de aceptacion

- El apartado interpreta resultados y no solo los enumera.
- Los puntos criticos quedan identificados por nudo, sistema y criterio de aceptacion.
- La sobrepresion de la Boca de Incendio Equipada 122 queda resuelta mediante valvula reductora, no como incumplimiento sin solucion.
- La comparativa RO1/RL no contradice la hipotesis final adoptada.

## Riesgos o huecos

- Debe resolverse la diferencia entre algunos valores del anexo de calculo y el informe final de auditoria.
- Falta decidir si la tabla normativa completa entra en cuerpo o se resume y se remite al anexo.
- La comparativa RO1/RL puede confundir si se introduce sin explicar que es una reflexion de diseno.

