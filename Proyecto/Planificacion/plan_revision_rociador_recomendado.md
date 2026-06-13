# Plan: Revisión del Rociador Recomendado bajo UNE-EN 12845

> Fuente de requisitos: solicitud del usuario en esta conversación y validación normativa en el notebook `PCI_Practicas`.

## Summary

Revisar la selección actual de rociador para sustituirla por un modelo que mantenga la misma hipótesis de diseño del proyecto, con:

- área de operación RO1 de `72 m2`
- cobertura objetivo de `24,01 m2` por rociador
- presión mínima residual inferior a `1,5 bar`
- factor K superior al rociador actual

La revisión debe apoyarse en `UNE-EN 12845`, especialmente en el marco de `tecnología especial / Anexo L`, y no debe usar `NFPA 25` como criterio de selección. La búsqueda de catálogos y fichas técnicas se hará con `Exa`. Después, se actualizarán los archivos de `Proyecto/Anotaciones/` relacionados con rociadores.

## Architectural Decisions

Decisiones que quedan fijadas para toda la revisión:

- **Norma base**: `UNE-EN 12845` y documentación de fabricante compatible con el marco del notebook `PCI_Practicas`.
- **Clasificación de diseño**: mantener `RO1`.
- **Criterio hidráulico**: mantener `72 m2` de área de operación y verificar la densidad exigida sobre la cobertura objetivo.
- **Búsqueda comercial**: usar `Exa` para localizar catálogos, páginas de producto y fichas técnicas.
- **Criterio de descarte**: excluir soluciones justificadas por `NFPA 25`, `ESFR/CMSA` de almacenamiento o reclasificación a `RL`.
- **Salida documental**: actualizar las anotaciones del proyecto que hoy describen el rociador anterior o contienen presiones, coberturas y justificaciones ya obsoletas.

---

## Phase 1: Localizar y comparar candidatos

**User stories**: encontrar un nuevo rociador compatible con la cobertura existente y una presión mínima residual menor.

### What to build

Buscar con `Exa` rociadores de cobertura ampliada, residencial o tecnología especial que puedan sostener la hipótesis del proyecto sin cambiar el área de operación. Registrar para cada candidato el fabricante, modelo, enlace al catálogo, ficha técnica, cobertura declarada, presión mínima residual y factor K.

### Acceptance criteria

- [ ] Hay una lista corta de candidatos comparables.
- [ ] Cada candidato tiene catálogo y ficha técnica localizados con `Exa`.
- [ ] Cada candidato se evalúa contra `UNE-EN 12845` y el notebook `PCI_Practicas`.
- [ ] Quedan descartados los candidatos apoyados en `NFPA 25` o en una reclasificación a `RL`.

---

## Phase 2: Validar la opción seleccionada

**User stories**: comprobar que el nuevo rociador cumple la normativa del notebook y mejora la condición hidráulica requerida.

### What to build

Seleccionar el candidato que mejor conserve la geometría del proyecto y verificar que su uso está respaldado por la ficha del fabricante y por la lógica normativa del notebook. Documentar la comprobación de presión mínima residual, el mantenimiento de `RO1`, la cobertura objetivo y la justificación de tecnología especial si aplica.

### Acceptance criteria

- [ ] La opción elegida mantiene `RO1` y la cobertura objetivo.
- [ ] La presión mínima residual queda por debajo de `1,5 bar` según la ficha consultada.
- [ ] El factor K es superior al rociador sustituido.
- [ ] La justificación normativa queda alineada con `UNE-EN 12845` y `PCI_Practicas`.

---

## Phase 3: Actualizar anotaciones del proyecto

**User stories**: dejar la documentación del proyecto consistente con la nueva selección de rociador.

### What to build

Actualizar los archivos de `Proyecto/Anotaciones/` que tratan la selección, la presión mínima, la cobertura, la justificación económica y la revisión normativa. La redacción debe eliminar referencias al rociador anterior, reflejar el nuevo modelo y mantener coherentes las relaciones entre norma, cobertura y presión.

### Acceptance criteria

- [ ] Se actualizan los documentos que hoy describen el rociador y sus parámetros.
- [ ] Los enlaces cruzados entre anotaciones siguen siendo correctos.
- [ ] No quedan menciones contradictorias al modelo anterior.
- [ ] La documentación deja claro que la búsqueda comercial se hizo con `Exa`.

---

## Test Plan

- Revisar que el rociador elegido aparece en una fuente de fabricante válida.
- Verificar con el notebook `PCI_Practicas` que la solución sigue apoyándose en `UNE-EN 12845`.
- Comprobar que la documentación actualizada no menciona `NFPA 25` como criterio de selección.
- Confirmar que los textos revisados conservan el área de operación y la cobertura objetivo.

## Assumptions

- La revisión documental no cambia la hidráulica base del proyecto más allá del rociador seleccionado.
- El nuevo modelo se elegirá por compatibilidad normativa y mejora de presión, no por afinidad de marca.
- Si aparecen varios modelos válidos, se priorizará el que requiera menos presión y preserve mejor la cobertura objetivo.
