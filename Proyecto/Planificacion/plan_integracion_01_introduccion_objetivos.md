# Plan de integracion: `01_introduccion_objetivos.md`

## Tarea objetivo

- Especificacion fuente: [01_introduccion_objetivos.md](../Especificaciones/01_introduccion_objetivos.md)
- Seccion destino: `Introduccion e objetivos`
- Salida primaria: Markdown cerrado en `Proyecto/Especificaciones/01_introduccion_objetivos.md`
- Salida posterior: fragmento LaTeX en `Practica_PCI_LaTeX/main.tex`, dentro de `\section{Introduccion e objetivos}`
- Agentes: [task-orchestrator](../../.agents/agents/task-orchestrator.md), [pci-researcher](../../.agents/agents/pci-researcher.md), [latex-writer](../../.agents/agents/latex-writer.md), [latex-validator](../../.agents/agents/latex-validator.md)

## Fuentes canonicas

- [Catalogos de BIEs y rociadores](../Anotaciones/catalogos-bies-rociadores.md)
- Normativa local: `../../Normativa/DBSI.pdf`
- Normativa local: `../../Normativa/Normas BIEs/`
- Normativa local: `../../Normativa/Normas Rociadores/`
- Figuras disponibles:
  - `../../Practica_PCI_LaTeX/Figuras/IPCI.png`
  - `../../Practica_PCI_LaTeX/Figuras/BIE_en_funcionamiento.png`
  - `../../Practica_PCI_LaTeX/Figuras/Rocioador_en_funcionamiento.png`
- Plantilla: `../../Practica_PCI_LaTeX/main.tex`

## Objetivo de integracion

Sustituir la introduccion minima actual por una introduccion continua que explique el contexto de la proteccion contra incendios, diferencie Bocas de Incendio Equipadas y rociadores automaticos, mantenga los tres objetivos originales de la practica y anada la interpretacion critica de resultados hidraulicos como objetivo transversal.

## Secuencia de agentes

### 1. `task-orchestrator`

```yaml
agente: task-orchestrator
tarea: Integrar 01_introduccion_objetivos.md en la seccion Introduccion e objetivos.
entradas:
  - Proyecto/Especificaciones/01_introduccion_objetivos.md
  - Proyecto/Anotaciones/catalogos-bies-rociadores.md
  - Normativa/DBSI.pdf
  - Normativa/Normas BIEs/
  - Normativa/Normas Rociadores/
  - Practica_PCI_LaTeX/main.tex
salida_esperada: Introduccion tecnicamente trazable y objetivos coherentes con la practica.
control: No ampliar con teoria general que no conecte con el edificio y los sistemas calculados.
```

### 2. `pci-researcher`

```yaml
agente: pci-researcher
seccion: Introduccion e objetivos
proposito: Reunir marco normativo y justificacion tecnica minima para introducir el sistema.
pedir:
  - Papel de CTE DB-SI, RIPCI, UNE-EN 671-1 y UNE-EN 12845.
  - Diferencia funcional entre Bocas de Incendio Equipadas y rociadores automaticos.
  - Identificacion de figuras utiles y figuras que deben quedar solo como material institucional.
  - Riesgo de mencionar caracter voluntario o sobredimensionado en la introduccion.
```

### 3. `latex-writer`

```yaml
agente: latex-writer
seccion: Introduccion e objetivos
fuente_markdown: Proyecto/Especificaciones/01_introduccion_objetivos.md
accion: Consolidar prosa introductoria, objetivos y figuras seleccionadas en la seccion existente.
restricciones:
  - Mantener continuidad entre contexto, alcance y objetivos.
  - Corregir la errata "realtivos" si se edita el texto actual.
  - Usar figuras solo si aportan contexto tecnico real.
```

### 4. `latex-validator`

```yaml
agente: latex-validator
artefacto: Practica_PCI_LaTeX/main.tex
accion: Validar coherencia semantica, rutas de figuras y compilacion.
checks:
  - Figuras con caption y label.
  - Sin rutas absolutas.
  - Objetivos alineados con BIEs, rociadores y analisis normativo.
```

## Fases de ejecucion

### Fase 1. Marco tecnico

- Definir el contexto de las instalaciones activas de PCI sin desarrollar teoria de relleno.
- Introducir CTE DB-SI, RIPCI, UNE-EN 671-1 y UNE-EN 12845 solo como marco de referencia.
- Separar claramente Bocas de Incendio Equipadas y rociadores automaticos.

### Fase 2. Alcance y objetivos

- Presentar que el edificio se modela con red comun, grupo de presion, Bocas de Incendio Equipadas y rociadores.
- Mantener los objetivos de diseno y calculo de Bocas de Incendio Equipadas, diseno y calculo de rociadores, y analisis normativo.
- Anadir interpretacion critica de resultados hidraulicos.

### Fase 3. Figuras

- Decidir si se integran `IPCI.png`, `BIE_en_funcionamiento.png` y `Rocioador_en_funcionamiento.png`.
- Usar pie `Fuente: Elaboracion grupal`.
- Mantener `chimenea_recta.jpg`, `ule.jpg` y `escudo-ingenierias.png` como material de portada o institucional.

### Fase 4. Consolidacion y validacion

- Insertar el texto en la seccion existente.
- Corregir la errata ya presente en `main.tex` si se modifica ese bloque.
- Validar compilacion si se aplican cambios LaTeX.

## Criterios de aceptacion

- La introduccion no parece una teoria aislada, sino una entrada directa a la practica.
- Los objetivos son claros, completos y coherentes con los resultados calculados.
- Las figuras, si se usan, existen y estan justificadas.
- No se modifica la estructura de secciones de `main.tex`.

## Riesgos o huecos

- Esta pendiente decidir si el caracter voluntario de la instalacion entra en la introduccion o se reserva para resultados/conclusiones.
- Las referencias normativas deben verificarse contra los PDFs locales o NotebookLM antes de cerrar citas formales.

