# Plan: Búsqueda y Verificación de Catálogos de BIEs y Rociadores

## Summary

El objetivo es localizar catálogos técnicos de fabricantes españoles o europeos para BIEs con manguera semirrígida y rociadores, contrastar cada producto contra la normativa aplicable recogida en `PCI_Practicas`, y consolidar los resultados en `Proyecto/Anotaciones/catalogos-bies-rociadores.md`.

La ejecución se divide en 4 fases verticales, cada una con un entregable verificable.

## Key Decisions

- **Fuentes de catálogo**: usar catálogos, fichas técnicas y documentación oficial de fabricantes españoles o europeos.
- **Fuentes fuera de España**: solo se aceptan si acreditan cumplimiento estricto de toda la normativa detallada en `PCI_Practicas`.
- **Entregable final**: archivo Markdown en `Proyecto/Anotaciones/catalogos-bies-rociadores.md`.
- **BIEs**: considerar únicamente BIEs con manguera semirrígida.
- **Rociadores**: clasificar por configuración de boquilla y por tipo de funcionamiento:
  - Sistemas con agua en contacto con el rociador.
  - Sistemas sin agua en contacto con el rociador, con aire a presión.
- **Trazabilidad**: cada producto aceptado debe incluir fabricante, país o ámbito de comercialización, modelo, enlace o referencia documental, parámetros técnicos relevantes y comprobación normativa.

## Implementation Phases

## Phase 1: Matriz de Requisitos Normativos

**User stories covered**: identificar qué condiciones debe cumplir cada tipo de producto antes de buscar catálogos.

### What to build

Crear una matriz de verificación con los requisitos normativos aplicables a BIEs semirrígidas y rociadores. La matriz servirá como checklist único para evaluar cada catálogo localizado, incluyendo una comprobación específica de adecuación a normativa española/europea.

### Acceptance criteria

- [ ] La matriz separa BIEs y rociadores.
- [ ] La matriz distingue rociadores con agua en contacto y rociadores con aire a presión.
- [ ] Cada requisito incluye criterio de aceptación y dato técnico que debe buscarse en catálogo.
- [ ] La matriz incluye un campo de cumplimiento normativo español/europeo.
- [ ] Los requisitos ambiguos quedan marcados como “pendiente de confirmación normativa”.

## Phase 2: Búsqueda y Verificación de BIEs Semirrígidas

**User stories covered**: encontrar catálogos de BIEs válidas y comprobar cumplimiento normativo.

### What to build

Buscar catálogos oficiales de fabricantes españoles o europeos de BIEs con manguera semirrígida, extraer los datos técnicos necesarios y validar cada modelo contra la matriz normativa. Los fabricantes europeos no españoles solo se aceptarán si la documentación permite verificar cumplimiento estricto de la normativa aplicable de `PCI_Practicas`.

### Acceptance criteria

- [ ] Se identifican varios fabricantes o modelos candidatos españoles o europeos.
- [ ] Cada BIE candidata incluye referencia documental oficial.
- [ ] Se verifica el país o ámbito normativo de comercialización.
- [ ] Se verifican las características normativas relevantes de la manguera semirrígida.
- [ ] Los modelos que no cumplan o no aporten datos suficientes se descartan con motivo documentado.
- [ ] Se seleccionan las opciones válidas con una tabla comparativa.

## Phase 3: Búsqueda y Verificación de Rociadores

**User stories covered**: encontrar configuraciones de rociadores según boquilla y funcionamiento, y validar cumplimiento normativo.

### What to build

Buscar catálogos oficiales de fabricantes españoles o europeos de rociadores y organizar las opciones por tipo de boquilla y funcionamiento. Para cada configuración, validar compatibilidad normativa y condiciones técnicas de uso. Los productos europeos no españoles solo se aceptarán si acreditan cumplimiento estricto de toda la normativa aplicable recogida en `PCI_Practicas`.

### Acceptance criteria

- [ ] Se diferencian configuraciones con agua en contacto y configuraciones con aire a presión.
- [ ] Se registran distintos tipos de boquilla o respuesta cuando el catálogo lo permita.
- [ ] Cada rociador candidato incluye referencia documental oficial.
- [ ] Se verifica el país o ámbito normativo de comercialización.
- [ ] Cada configuración se evalúa contra la matriz normativa.
- [ ] Se documentan modelos aceptados, descartados y dudas técnicas pendientes.

## Phase 4: Consolidación del Markdown Final

**User stories covered**: entregar una anotación clara, trazable y reutilizable para el proyecto.

### What to build

Redactar `Proyecto/Anotaciones/catalogos-bies-rociadores.md` con metodología, matriz normativa resumida, resultados de BIEs, resultados de rociadores, tablas comparativas y conclusiones de selección. El documento debe dejar claro qué fuentes son españolas, cuáles son europeas no españolas, y cómo se ha verificado su cumplimiento normativo.

### Acceptance criteria

- [ ] El Markdown contiene una sección de metodología.
- [ ] Incluye tablas separadas para BIEs y rociadores.
- [ ] Cada producto válido tiene fabricante, país o ámbito de comercialización, modelo, fuente, parámetros revisados y conclusión de cumplimiento.
- [ ] Cada producto europeo no español incluye justificación explícita de cumplimiento estricto de la normativa de `PCI_Practicas`.
- [ ] Cada descarte incluye motivo.
- [ ] La conclusión recomienda configuraciones válidas para usar en la práctica.
- [ ] El archivo queda preparado para auditoría posterior, con enlaces o referencias suficientes.

## Test Plan

- Revisar que cada producto aceptado tenga fuente oficial trazable.
- Comprobar que las fuentes sean españolas o europeas.
- Verificar que los productos europeos no españoles acrediten cumplimiento estricto de la normativa indicada.
- Comprobar que ningún producto marcado como válido tenga campos normativos críticos vacíos.
- Verificar que las BIEs incluidas sean de manguera semirrígida.
- Verificar que los rociadores estén clasificados por funcionamiento y boquilla.
- Revisar que las conclusiones no contradigan la matriz normativa.
- Confirmar que el Markdown final se abre correctamente y que sus tablas son legibles.

## Assumptions

- Se priorizan fabricantes españoles cuando existan opciones suficientes.
- Se admiten fabricantes europeos si su documentación permite comprobar cumplimiento completo de la normativa aplicable.
- No se aceptan catálogos no europeos salvo instrucción posterior expresa.
- Si un catálogo no aporta datos suficientes para verificar un requisito crítico, el producto se marca como no verificable.
- “Con agua en contacto” se tratará como configuración equivalente a sistema húmedo.
- “Sin agua en contacto, con aire a presión” se tratará como configuración equivalente a sistema seco o de tubería presurizada con aire.
- El entregable final será una anotación técnica, no una memoria completa del proyecto.
