# Plan de activacion secuencial de integracion de memoria

## Proposito

Este plan maestro define como activar de forma secuencial los planes de integracion de la memoria tecnica PCI a partir de las especificaciones modulares de `Proyecto/Especificaciones/`, usando como punto de entrada el agente [`task-orchestrator`](../../.agents/agents/task-orchestrator.md).

La estrategia de trabajo es cerrar primero todos los Markdown modulares y realizar despues una unica consolidacion editorial global en `Practica_PCI_LaTeX/main.tex`. De este modo, la capa tecnica queda estabilizada antes de modificar la memoria LaTeX.

## Fuentes de planificacion

- [Indice de planes de integracion](planes_integracion_memoria_especificaciones.md)
- [Plan de integracion del resumen](plan_integracion_00_resumen.md)
- [Plan de integracion de introduccion y objetivos](plan_integracion_01_introduccion_objetivos.md)
- [Plan de integracion de metodologia](plan_integracion_02_metodologia.md)
- [Plan de integracion de resultados y discusion](plan_integracion_03_resultados_discusion.md)
- [Plan de integracion de conclusiones](plan_integracion_04_conclusiones.md)
- [Task Orchestrator](../../.agents/agents/task-orchestrator.md)
- [Anotaciones tecnicas](../Anotaciones/)
- NotebookLM `PCI_Practica` o `PCI_Practicas`, resuelto mediante `nlm-skill`

## Decision de arquitectura documental

- **Salida primaria**: Markdown cerrado en `Proyecto/Especificaciones/`.
- **Salida editorial posterior**: consolidacion global en `Practica_PCI_LaTeX/main.tex`.
- **Orquestacion**: toda activacion empieza con `task-orchestrator`.
- **Investigacion tecnica**: `task-orchestrator` delega en `pci-researcher` cuando falte trazabilidad o haya discrepancias.
- **Consolidacion LaTeX**: `latex-writer` solo se invoca cuando los cinco Markdown esten cerrados.
- **Validacion LaTeX**: `latex-validator` se invoca al final sobre el artefacto LaTeX consolidado.
- **Plantilla**: no se reestructura `Practica_PCI_LaTeX/main.tex`; se rellenan los bloques existentes.
- **Referencias normativas**: antes de consolidar LaTeX se revisan `Proyecto/Anotaciones/` y NotebookLM para recopilar normativa, manuales y catalogos usados. Las referencias finales se redactan en formato IEEE propio de normativa o documentacion tecnica, sin fechas de acceso ni enlaces web.

## Secuencia de activacion

### Fase 0. Preflight documental

**Objetivo**: comprobar que el flujo puede arrancar sin redefinir la estructura del proyecto.

**Entradas**:

- `Proyecto/Planificacion/planes_integracion_memoria_especificaciones.md`
- `Proyecto/Especificaciones/00_resumen.md`
- `Proyecto/Especificaciones/01_introduccion_objetivos.md`
- `Proyecto/Especificaciones/02_metodologia.md`
- `Proyecto/Especificaciones/03_resultados_discusion.md`
- `Proyecto/Especificaciones/04_conclusiones.md`
- `Practica_PCI_LaTeX/main.tex`

**Checks**:

- Confirmar que existen las cinco especificaciones.
- Confirmar que los planes de integracion apuntan a secciones reales de `main.tex`.
- Registrar pendientes transversales antes de cerrar Markdown:
  - discrepancias entre valores historicos de `Proyecto/resultados_calculos.md` y el informe final de auditoria;
  - decision sobre tablas resumidas en metodologia y resultados;
  - decision sobre uso de figuras tecnicas;
  - enlaces web citados en `Proyecto/Anotaciones/` que deban convertirse en referencias bibliograficas formales;
  - tratamiento de la comparativa RO1/RL;
  - tono final de conclusiones;
  - mencion o no del caracter voluntario o sobredimensionado.

**Criterio de salida**:

- El orquestador puede abrir la primera seccion sin crear nuevas fuentes ni modificar LaTeX.

### Fase N. Cierre normativo y bibliografico

**Momento de ejecucion**: despues de cerrar los Markdown tecnicos y antes de la consolidacion LaTeX global.

**Objetivo**: recopilar toda la normativa, manuales y documentacion tecnica empleada en el proyecto, contrastarla con NotebookLM y dejarla lista para citarse correctamente en la memoria.

**Entradas locales obligatorias**:

- `Proyecto/Anotaciones/`
- `Proyecto/Especificaciones/`
- `Proyecto/resultados_calculos.md`
- `Normativa/`
- `Practica_PCI_LaTeX/refs.bib`

**Revision de enlaces web en anotaciones**:

- Buscar enlaces `http`, `https` y `www` en `Proyecto/Anotaciones/`.
- Identificar si cada enlace corresponde a normativa, manual de software, catalogo tecnico, ficha de fabricante o material auxiliar.
- Sustituir el uso editorial de enlaces web por una referencia formal a la norma, manual, catalogo o ficha tecnica que corresponda.
- No trasladar a la memoria final fechas de acceso ni URLs cuando la referencia sea normativa o documentacion tecnica estable.

**Invocacion de `nlm-skill`**:

```yaml
skill: nlm-skill
proposito: Conectar con NotebookLM y contrastar la normativa empleada en el proyecto.
notebook_objetivo: PCI_Practica
fallback_notebook: PCI_Practicas
flujo:
  - Ejecutar nlm login o nlm login --check antes de consultar.
  - Ejecutar nlm alias list y nlm notebook list si el alias PCI_Practica no existe.
  - Resolver el notebook operativo como PCI_Practica o, si el repositorio lo nombra asi, PCI_Practicas.
  - Usar nlm notebook query para pedir la lista de normativa, manuales y documentacion tecnica citada o usada en el proyecto.
  - No usar nlm chat start.
```

**Consulta minima a NotebookLM**:

```text
Recopila toda la normativa, manuales, catalogos y fichas tecnicas empleados en el proyecto de proteccion contra incendios. Para cada fuente indica titulo oficial, organismo o fabricante, numero de norma o codigo documental si existe, edicion o fecha documental si aparece en la fuente, sistema al que aplica y apartado de la memoria donde debe citarse.
```

**Formato bibliografico requerido**:

- Usar formato IEEE adaptado a normativa y documentacion tecnica.
- Para normas: organismo, titulo de la norma, codigo de norma, edicion o anio si consta.
- Para reales decretos o codigos tecnicos: entidad emisora, titulo oficial, identificador legal o documento basico, anio si consta.
- Para catalogos o fichas tecnicas: fabricante, titulo de ficha o catalogo, codigo documental o modelo, revision o fecha documental si consta.
- No incluir `Disponible en:`, URLs, enlaces web ni fechas de acceso.

**Ejemplos de forma esperada**:

- `[n] UNE, Sistemas fijos de lucha contra incendios. Sistemas de rociadores automaticos. Diseno, instalacion y mantenimiento, UNE-EN 12845.`
- `[n] Ministerio de Vivienda, Codigo Tecnico de la Edificacion, Documento Basico SI: Seguridad en caso de incendio.`
- `[n] Tyco Fire Products, Series EC-11 and EC-14 Extended Coverage Upright and Pendent Sprinklers, Data Sheet TFP220.`

**Criterio de salida**:

- Lista unica de referencias normativas y tecnicas lista para `refs.bib` o para el apartado bibliografico que use la memoria.
- Confirmacion de que las citas del cuerpo no dependen de enlaces web.
- Identificacion de fuentes locales o de NotebookLM que sigan incompletas.

### Fase 1. Activar `00_resumen.md`

**Plan base**: [plan_integracion_00_resumen.md](plan_integracion_00_resumen.md)

**Orden para `task-orchestrator`**:

```yaml
agente: task-orchestrator
tarea: Activar el plan de integracion 00_resumen para cerrar la especificacion del Resumen.
entradas:
  - Proyecto/Planificacion/plan_integracion_00_resumen.md
  - Proyecto/Especificaciones/00_resumen.md
  - Proyecto/resultados_calculos.md
  - Proyecto/Anotaciones/informe_revision_normativa_resultados_calculos.md
  - Practica_PCI_LaTeX/main.tex
salida_esperada: Markdown del resumen cerrado y apto para consolidacion LaTeX posterior.
control:
  - No modificar Practica_PCI_LaTeX/main.tex.
  - No anadir referencias, listas, tablas ni ecuaciones.
  - No usar abreviaturas.
```

**Compuerta de cierre**:

- El resumen no supera 250 palabras.
- Los valores finales quedan congelados.
- No quedan pendientes antes de pasar a LaTeX.

### Fase 2. Activar `01_introduccion_objetivos.md`

**Plan base**: [plan_integracion_01_introduccion_objetivos.md](plan_integracion_01_introduccion_objetivos.md)

**Orden para `task-orchestrator`**:

```yaml
agente: task-orchestrator
tarea: Activar el plan de integracion 01_introduccion_objetivos para cerrar la especificacion de Introduccion e objetivos.
entradas:
  - Proyecto/Planificacion/plan_integracion_01_introduccion_objetivos.md
  - Proyecto/Especificaciones/01_introduccion_objetivos.md
  - Proyecto/Anotaciones/catalogos-bies-rociadores.md
  - Normativa/DBSI.pdf
  - Normativa/Normas BIEs/
  - Normativa/Normas Rociadores/
  - Practica_PCI_LaTeX/main.tex
salida_esperada: Markdown de introduccion y objetivos cerrado y coherente con el alcance de la practica.
control:
  - No modificar Practica_PCI_LaTeX/main.tex.
  - No ampliar con teoria general desconectada del edificio y los sistemas calculados.
  - Resolver si el caracter voluntario o sobredimensionado se excluye de esta seccion.
```

**Compuerta de cierre**:

- Los objetivos cubren Bocas de Incendio Equipadas, rociadores, analisis de resultados y comprobacion normativa.
- Las referencias normativas quedan tratadas como marco de apoyo, no como desarrollo teorico extenso.
- Las figuras que pasaran a LaTeX quedan seleccionadas o descartadas.

### Fase 3. Activar `02_metodologia.md`

**Plan base**: [plan_integracion_02_metodologia.md](plan_integracion_02_metodologia.md)

**Orden para `task-orchestrator`**:

```yaml
agente: task-orchestrator
tarea: Activar el plan de integracion 02_metodologia para cerrar la especificacion de Metodologia y subsecciones.
entradas:
  - Proyecto/Planificacion/plan_integracion_02_metodologia.md
  - Proyecto/Especificaciones/02_metodologia.md
  - Proyecto/resultados_calculos.md
  - Proyecto/Anotaciones/superficie-rociadores.md
  - Proyecto/Anotaciones/catalogos-bies-rociadores.md
  - Proyecto/Anotaciones/sobre_altura_cotas.md
  - Proyecto/Anotaciones/presion-minima-rociador-dmelect.md
  - Practica_PCI_LaTeX/main.tex
salida_esperada: Markdown metodologico cerrado para Datos introducidos, Topologia, Trazado, Equipos y Materiales.
control:
  - No modificar Practica_PCI_LaTeX/main.tex.
  - No mezclar justificacion de resultados con metodologia.
  - Cerrar la decision sobre tabla resumida de datos de entrada.
```

**Compuerta de cierre**:

- El modelo hidraulico queda reproducible conceptualmente.
- La superficie protegida de rociadores se usa solo como alcance fisico, no como sustituto del area normativa de operacion.
- Equipos, materiales y figuras quedan trazados a fuentes existentes.

### Fase 4. Activar `03_resultados_discusion.md`

**Plan base**: [plan_integracion_03_resultados_discusion.md](plan_integracion_03_resultados_discusion.md)

**Orden para `task-orchestrator`**:

```yaml
agente: task-orchestrator
tarea: Activar el plan de integracion 03_resultados_discusion para cerrar la especificacion de Resultados y discusion.
entradas:
  - Proyecto/Planificacion/plan_integracion_03_resultados_discusion.md
  - Proyecto/Especificaciones/03_resultados_discusion.md
  - Proyecto/resultados_calculos.md
  - Proyecto/Anotaciones/informe_revision_normativa_resultados_calculos.md
  - Proyecto/Anotaciones/comparativa_riesgo_ordinario_vs_ligero.md
  - Proyecto/Anotaciones/presion-minima-rociador-dmelect.md
  - Proyecto/Anotaciones/justificacion_simultaneidad_BIEs.md
  - Proyecto/Anotaciones/informe_revision_calculos_bie.md
  - Practica_PCI_LaTeX/main.tex
salida_esperada: Markdown de resultados cerrado, con mapa de estados, puntos desfavorables y verificacion normativa resumida.
control:
  - No modificar Practica_PCI_LaTeX/main.tex.
  - Separar siempre Bocas de Incendio Equipadas y rociadores automaticos.
  - Congelar los valores finales antes de redactar el cierre.
```

**Compuerta de cierre**:

- El apartado interpreta resultados, no solo los enumera.
- Los puntos criticos quedan identificados por sistema, nudo y criterio de aceptacion.
- La valvula reductora de la Boca de Incendio Equipada 122 queda tratada como medida puntual.
- La comparativa RO1/RL no aparece como contradiccion de la hipotesis final.

### Fase 5. Activar `04_conclusiones.md`

**Plan base**: [plan_integracion_04_conclusiones.md](plan_integracion_04_conclusiones.md)

**Orden para `task-orchestrator`**:

```yaml
agente: task-orchestrator
tarea: Activar el plan de integracion 04_conclusiones para cerrar la especificacion de Conclusiones.
entradas:
  - Proyecto/Planificacion/plan_integracion_04_conclusiones.md
  - Proyecto/Especificaciones/04_conclusiones.md
  - Proyecto/resultados_calculos.md
  - Proyecto/Anotaciones/informe_revision_normativa_resultados_calculos.md
  - Proyecto/Anotaciones/catalogos-bies-rociadores.md
  - Practica_PCI_LaTeX/main.tex
salida_esperada: Markdown de conclusiones cerrado y coherente con objetivos, metodologia y resultados.
control:
  - No modificar Practica_PCI_LaTeX/main.tex.
  - No anadir figuras ni tablas.
  - No introducir datos o argumentos por primera vez.
```

**Compuerta de cierre**:

- Las conclusiones cierran todos los objetivos de la introduccion.
- No repiten literalmente resultados.
- La valvula reductora queda reconocida como condicion de ejecucion.
- El tono queda fijado como redaccion continua salvo instruccion expresa del tutor.

### Fase 6. Consolidacion LaTeX global

**Objetivo**: transformar los cinco Markdown cerrados en contenido editorial dentro de `Practica_PCI_LaTeX/main.tex`.

**Orden para `task-orchestrator`**:

```yaml
agente: task-orchestrator
tarea: Consolidar globalmente en LaTeX las cinco especificaciones cerradas de la memoria PCI.
entradas:
  - Proyecto/Especificaciones/00_resumen.md
  - Proyecto/Especificaciones/01_introduccion_objetivos.md
  - Proyecto/Especificaciones/02_metodologia.md
  - Proyecto/Especificaciones/03_resultados_discusion.md
  - Proyecto/Especificaciones/04_conclusiones.md
  - Lista normativa y bibliografica cerrada en la Fase N
  - Practica_PCI_LaTeX/refs.bib
  - Practica_PCI_LaTeX/main.tex
salida_esperada: main.tex actualizado dentro de la estructura existente.
control:
  - Invocar latex-writer solo en esta fase.
  - No crear secciones principales nuevas.
  - Corregir erratas locales en bloques editados.
  - Mantener rutas relativas reales para figuras.
  - Referenciar normativa y documentacion tecnica con formato IEEE sin URLs ni fechas de acceso.
```

**Trabajo esperado de `latex-writer`**:

- Insertar el resumen en `\section*{Resumen}`.
- Insertar introduccion y objetivos en `\section{Introduccion e objetivos}`.
- Distribuir metodologia entre la seccion principal y sus subsecciones existentes.
- Distribuir resultados entre `Resultados y discusion`, `Analisis de la verificacion hidraulica mediante mapa de estados` y `Analisis de los puntos singulares mas desfavorables`.
- Insertar conclusiones en `\section{Conclusiones}`.

**Validacion final con `latex-validator`**:

- Validacion semantica contra las especificaciones cerradas.
- Validacion estatica de figuras, tablas, labels, rutas relativas y ausencia de preambulo nuevo.
- Validacion bibliografica de referencias IEEE sin enlaces web ni fechas de acceso para normativa.
- Compilacion de `Practica_PCI_LaTeX/main.tex` si el contexto es compilable.

## Criterios de aceptacion global

- Las cinco especificaciones quedan cerradas antes de tocar LaTeX.
- No quedan pendientes bloqueantes en los Markdown.
- Los valores finales son coherentes entre resumen, resultados y conclusiones:
  - grupo de presion: 10,53 L/s y 99,63 mca;
  - reserva total: 37.906,87 L;
  - Boca de Incendio Equipada critica: nudo 125, con 2,000 bar en boquilla;
  - rociador critico: nudo 142, con 2,829 bar.
- `Practica_PCI_LaTeX/main.tex` mantiene su estructura editorial.
- Las referencias normativas y tecnicas no contienen URLs ni fechas de acceso.
- La validacion final no detecta contradicciones entre metodologia, resultados y conclusiones.

## Riesgos y controles

- **Discrepancias numericas**: congelar valores contra el informe final de auditoria antes de cerrar resumen, resultados y conclusiones.
- **LaTeX prematuro**: prohibir cambios en `main.tex` durante las fases 1 a 5.
- **Expansion teorica**: limitar introduccion y metodologia a lo necesario para la practica.
- **RO1/RL**: tratarlo solo como reflexion tecnica si se mantiene en resultados, nunca como decision pendiente.
- **Figuras**: usar solo archivos existentes y con utilidad tecnica clara.
- **Referencias web en anotaciones**: revisarlas como pista de fuente, no copiarlas como enlaces en la memoria.
- **NotebookLM**: consultar `PCI_Practica` o `PCI_Practicas` con `nlm-skill` para cerrar la lista normativa antes de LaTeX.
- **Conclusiones**: no introducir argumentos que no hayan aparecido en metodologia o resultados.
