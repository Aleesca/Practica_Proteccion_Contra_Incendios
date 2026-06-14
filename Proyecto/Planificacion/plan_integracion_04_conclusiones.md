# Plan de integracion: `04_conclusiones.md`

## Tarea objetivo

- Especificacion fuente: [04_conclusiones.md](../Especificaciones/04_conclusiones.md)
- Seccion destino: `Conclusiones`
- Salida primaria: Markdown cerrado en `Proyecto/Especificaciones/04_conclusiones.md`
- Salida posterior: fragmento LaTeX en `Practica_PCI_LaTeX/main.tex`, dentro de `\section{Conclusiones}`
- Agentes: [task-orchestrator](../../.agents/agents/task-orchestrator.md), [pci-researcher](../../.agents/agents/pci-researcher.md), [latex-writer](../../.agents/agents/latex-writer.md), [latex-validator](../../.agents/agents/latex-validator.md)

## Fuentes canonicas

- [Resultados de calculo](../resultados_calculos.md)
- [Revision normativa y resultados de calculos](../Anotaciones/informe_revision_normativa_resultados_calculos.md)
- [Catalogos de BIEs y rociadores](../Anotaciones/catalogos-bies-rociadores.md)
- Anexos de `../../Practica_PCI_LaTeX/main.tex`
- Plantilla: `../../Practica_PCI_LaTeX/main.tex`

## Objetivo de integracion

Cerrar la memoria con una valoracion tecnica que confirme que se han alcanzado los objetivos, que los puntos mas desfavorables cumplen y que las decisiones de trazado, diametros, grupo de presion, reserva y valvula reductora quedan justificadas. No debe introducir datos nuevos ni figuras.

## Secuencia de agentes

### 1. `task-orchestrator`

```yaml
agente: task-orchestrator
tarea: Integrar 04_conclusiones.md en la seccion Conclusiones.
entradas:
  - Proyecto/Especificaciones/04_conclusiones.md
  - Proyecto/resultados_calculos.md
  - Proyecto/Anotaciones/informe_revision_normativa_resultados_calculos.md
  - Proyecto/Anotaciones/catalogos-bies-rociadores.md
  - Practica_PCI_LaTeX/main.tex
salida_esperada: Cierre tecnico coherente con objetivos, metodologia y resultados.
control: No anadir figuras ni ampliar con nuevos argumentos no tratados antes.
```

### 2. `pci-researcher`

```yaml
agente: pci-researcher
seccion: Conclusiones
proposito: Confirmar que las conclusiones usan solo datos ya trazados en resultados y metodologia.
pedir:
  - Valores finales de nudos criticos, grupo de presion, reserva y velocidad maxima.
  - Decision de valvula reductora en la Boca de Incendio Equipada 122.
  - Respaldo documental de equipos y anexos.
  - Advertencia sobre datos que no deben aparecer por primera vez en conclusiones.
```

### 3. `latex-writer`

```yaml
agente: latex-writer
seccion: Conclusiones
fuente_markdown: Proyecto/Especificaciones/04_conclusiones.md
accion: Consolidar el cierre en prosa dentro de la seccion existente.
restricciones:
  - Sin figuras nuevas.
  - Sin tablas salvo orden explicita.
  - No repetir literalmente la seccion de resultados.
```

### 4. `latex-validator`

```yaml
agente: latex-validator
artefacto: Practica_PCI_LaTeX/main.tex
accion: Validar coherencia final y compilacion.
checks:
  - Cifras finales coincidentes con resultados.
  - No aparicion de argumentos nuevos no justificados.
  - Cierre coherente con objetivos iniciales.
```

## Fases de ejecucion

### Fase 1. Cierre de objetivos

- Confirmar que se menciona el diseno y calculo de Bocas de Incendio Equipadas.
- Confirmar que se menciona el diseno y calculo de rociadores automaticos.
- Confirmar que se menciona la comprobacion hidraulica y normativa.

### Fase 2. Sintesis tecnica

- Incluir nudo 125 como Boca de Incendio Equipada mas desfavorable con 2,000 bar en boquilla.
- Incluir nudo 142 como rociador mas desfavorable con 2,829 bar.
- Incluir grupo de presion de 10,53 L/s y 99,63 mca.
- Incluir reserva total de 37.906,87 L.
- Incluir velocidad maxima de 8,62 m/s por debajo del limite de referencia.

### Fase 3. Decision constructiva

- Mencionar que la Boca de Incendio Equipada 122 requiere valvula reductora de presion.
- Explicar que esta decision permite mantener trazado y diametros calculados.
- Remitir calculos, planos y fichas tecnicas a anexos.

### Fase 4. Ajuste editorial

- Evitar repetir parrafos de resultados.
- Mantener una redaccion continua salvo que el tutor pida conclusiones numeradas.
- No introducir comparativa RO1/RL salvo que ya haya quedado tratada en resultados.

### Fase 5. Validacion

- Comprobar que ningun dato aparece por primera vez en conclusiones.
- Compilar tras la insercion LaTeX.

## Criterios de aceptacion

- Las conclusiones cierran todos los objetivos de la introduccion.
- No incorporan figuras ni argumentos nuevos.
- Los valores numericos son consistentes con el apartado de resultados.
- El texto reconoce la valvula reductora de la Boca de Incendio Equipada 122 como condicion de ejecucion.

## Riesgos o huecos

- Esta pendiente decidir si el cierre debe mencionar el caracter voluntario o sobredimensionado de la instalacion.
- El tono debe evitar repetir demasiado la seccion de resultados.
- Puede ser necesario ajustar a formato numerado si lo exige el tutor.

