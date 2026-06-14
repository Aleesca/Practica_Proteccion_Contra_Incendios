# Plan de integracion: `02_metodologia.md`

## Tarea objetivo

- Especificacion fuente: [02_metodologia.md](../Especificaciones/02_metodologia.md)
- Secciones destino:
  - `Metodologia`
  - `Datos introducidos en el programa`
  - `Topologia del edificio y seleccion del esquema de instalacion`
  - `Justificacion del trazado elegido`
  - `Equipos instalados y materiales de la instalacion`
- Salida primaria: Markdown cerrado en `Proyecto/Especificaciones/02_metodologia.md`
- Salida posterior: fragmentos LaTeX en `Practica_PCI_LaTeX/main.tex`
- Agentes: [task-orchestrator](../../.agents/agents/task-orchestrator.md), [pci-researcher](../../.agents/agents/pci-researcher.md), [latex-writer](../../.agents/agents/latex-writer.md), [latex-validator](../../.agents/agents/latex-validator.md)

## Fuentes canonicas

- [Resultados de calculo](../resultados_calculos.md)
- [Superficie de rociadores](../Anotaciones/superficie-rociadores.md)
- [Catalogos de BIEs y rociadores](../Anotaciones/catalogos-bies-rociadores.md)
- [Altura y cotas](../Anotaciones/sobre_altura_cotas.md)
- [Presion minima de rociador en DMELECT](../Anotaciones/presion-minima-rociador-dmelect.md)
- Figuras:
  - `../../Practica_PCI_LaTeX/Figuras/definicion_plantas.png`
  - `../../Practica_PCI_LaTeX/Figuras/Perfil_Plantas.png`
  - `../../Practica_PCI_LaTeX/Figuras/Inicio_Tramo_y_BIE.png`
- Anexos:
  - `../../Practica_PCI_LaTeX/Figuras/catalogos/ficha_tecnica_BIE.pdf`
  - `../../Practica_PCI_LaTeX/Figuras/catalogos/TFP220_06_2025.pdf`
- Plantilla: `../../Practica_PCI_LaTeX/main.tex`

## Objetivo de integracion

Construir el apartado metodologico que explique como se define el modelo hidraulico, como se representa el edificio, por que se adopta el trazado y que equipos/materiales quedan seleccionados. Debe conectar los datos de entrada con los resultados posteriores sin anticipar toda la discusion.

## Secuencia de agentes

### 1. `task-orchestrator`

```yaml
agente: task-orchestrator
tarea: Integrar 02_metodologia.md en Metodologia y sus subsecciones.
entradas:
  - Proyecto/Especificaciones/02_metodologia.md
  - Proyecto/resultados_calculos.md
  - Proyecto/Anotaciones/superficie-rociadores.md
  - Proyecto/Anotaciones/catalogos-bies-rociadores.md
  - Proyecto/Anotaciones/sobre_altura_cotas.md
  - Proyecto/Anotaciones/presion-minima-rociador-dmelect.md
  - Practica_PCI_LaTeX/main.tex
salida_esperada: Metodologia lista para consolidacion LaTeX por subsecciones existentes.
control: No mezclar justificacion de resultados con metodologia salvo como condicion de entrada.
```

### 2. `pci-researcher`

```yaml
agente: pci-researcher
seccion: Metodologia
proposito: Extraer datos de entrada, criterios de modelado, seleccion de equipos y vacios de trazabilidad.
pedir:
  - Metodo de calculo, perdidas secundarias, velocidad maxima y materiales.
  - Cotas, plantas, nudos, montantes y derivaciones relevantes.
  - Superficie protegida de rociadores y advertencia sobre area de operacion normativa.
  - Fichas de BIE IMP Workfire 300/B2 y rociador Tyco Series EC-11.
  - Figuras existentes que pueden sostener la explicacion metodologica.
```

### 3. `latex-writer`

```yaml
agente: latex-writer
seccion: Metodologia
fuente_markdown: Proyecto/Especificaciones/02_metodologia.md
accion: Transformar el Markdown final en fragmentos para las subsecciones existentes.
restricciones:
  - No crear nuevas secciones principales.
  - Usar figuras con rutas relativas reales.
  - Usar tablas solo si resumen datos de entrada o equipos con claridad.
```

### 4. `latex-validator`

```yaml
agente: latex-validator
artefacto: Practica_PCI_LaTeX/main.tex
accion: Validar sintaxis LaTeX, rutas de figuras, tablas y coherencia con metodologia.
checks:
  - Figuras con caption y label.
  - Tablas con caption y label si se anaden.
  - No anticipar conclusiones en metodologia.
```

## Fases de ejecucion

### Fase 1. Datos introducidos en el programa

- Documentar Hazen-Williams como metodo de calculo.
- Incluir perdidas secundarias del 20 %, velocidad maxima de referencia de 10 m/s y tuberia de acero con C = 120.
- Explicar nudos, ramas, longitudes, diametros, elementos terminales y grupo de presion.
- Separar criterios de Bocas de Incendio Equipadas y rociadores.

### Fase 2. Topologia y esquema de instalacion

- Explicar red comun alimentada por grupo de presion.
- Describir montante principal, derivaciones por planta, zonas comunes, viviendas y ramales de rociadores.
- Relacionar planta, perfil vertical y esquema unifilar.
- Integrar `definicion_plantas.png` y `Perfil_Plantas.png` si aportan claridad.

### Fase 3. Justificacion del trazado

- Justificar recorridos, continuidad hidraulica, accesibilidad y cobertura.
- Incluir que la superficie protegida para rociadores es 270,882 m2.
- Aclarar que esa superficie no sustituye al area de operacion hidraulica normativa.
- Explicar que las velocidades quedan dentro del limite de calculo sin cambiar diametros generales.

### Fase 4. Equipos y materiales

- Presentar la Boca de Incendio Equipada 25 mm IMP Workfire 300/B2.
- Presentar el rociador Tyco Series EC-11, SIN TY5237, K = 161,3 y presion minima residual de ficha 0,83 bar, documentada como 0,8 bar.
- Remitir las fichas tecnicas a anexos sin copiar el catalogo completo.
- Identificar tuberia de acero y coeficiente Hazen-Williams.

### Fase 5. Validacion

- Verificar que cada afirmacion de equipo o criterio esta respaldada por anotacion o anexo.
- Compilar solo despues de la insercion LaTeX.

## Criterios de aceptacion

- La metodologia permite reproducir conceptualmente el modelo sin volcar todas las tablas del anexo.
- La superficie de 270,882 m2 se usa solo como superficie fisica protegida.
- Los equipos seleccionados estan respaldados por fichas tecnicas.
- Las figuras existen y tienen pie `Fuente: Elaboracion grupal`.

## Riesgos o huecos

- Falta decidir si se incluye una tabla resumida de datos de entrada o si todo se remite al anexo.
- Hay que revisar los nombres exactos de figuras antes de escribir LaTeX.
- La clase de riesgo de rociadores debe tratarse con cautela si no queda cerrada formalmente por alcance/normativa.

