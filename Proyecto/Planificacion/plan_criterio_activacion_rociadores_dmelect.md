# Plan: Criterio de Activacion de Rociadores en DMelect

> Source PRD: solicitud en conversacion sobre la seleccion de rociadores a activar en la ultima planta para simulaciones DMelect

## Architectural decisions

Durable decisions that apply across all phases:

- **Fuente normativa**: usar `PCI_Practicas` como referencia principal para confirmar la clasificacion R01, el area de operacion de `72 m^2` y los criterios de simultaneidad aplicables.
- **Fuente tecnica de software**: consultar `DMelect_Guide` para determinar como representar en el programa los rociadores activos, la zona de calculo y el criterio de seleccion manual o semiautomatica.
- **Fuente de proyectos reales**: contrastar el criterio con ejemplos localizados mediante Exa para verificar como se resuelve la seleccion de rociadores en casos reales.
- **Criterio de trabajo**: la ultima planta se toma como zona mas desfavorable por altura y perdida de presion, pero la activacion debe representar un incendio localizado, no la ocupacion completa de la planta.
- **Resultado esperado**: un protocolo justificativo que explique que rociadores activar en DMelect, con criterio reproducible y trazable, sin modificar el modelo de instalacion.

---

## Phase 1: Confirmacion normativa del area de operacion

**User stories**: justificar que el incendio de simulacion no debe activar todos los rociadores de la planta.

### What to build

Verificar en `PCI_Practicas` que para la clasificacion R01 el area de cobertura u operacion a considerar es `72 m^2`, y aclarar la diferencia entre area normativa de calculo y cobertura geometrica de cada rociador.

Definir si el numero de rociadores activos debe derivarse del area que cubren y de su disposicion real en la vivienda, en vez de activarlos todos por planta.

### Acceptance criteria

- [ ] Queda confirmado el valor normativo de `72 m^2` para R01 o su equivalente exacto si el cuaderno usa otra formulacion.
- [ ] Se distingue de forma explicita entre area de operacion, superficie protegida y numero de rociadores activos.
- [ ] Se documenta por que no corresponde activar todos los rociadores de la planta en una hipotesis normal de incendio.

---

## Phase 2: Lectura operativa de DMelect

**User stories**: saber como introducir en DMelect el conjunto correcto de rociadores activos.

### What to build

Revisar `DMelect_Guide` para localizar el flujo de trabajo de simulacion de rociadores: seleccion manual, zonas remotas, hipotesis de calculo o cualquier mecanismo equivalente.

Traducir esa lectura a un procedimiento operativo para la ultima planta: como escoger rociadores, como reflejar el area de operacion y como evitar una activacion artificialmente amplia.

### Acceptance criteria

- [ ] Se identifica el mecanismo de DMelect que permite definir la hipotesis de incendio.
- [ ] Se aclara si la seleccion es manual, por zona o por criterio automatico.
- [ ] Queda definido el paso operativo necesario para reproducir la hipotesis en el programa.

---

## Phase 3: Contraste con casos reales

**User stories**: validar que el criterio no sea solo teorico.

### What to build

Buscar con Exa proyectos reales, memorias tecnicas o ejemplos de calculo en los que se muestre como se eligen los rociadores activos en una hipotesis de calculo.

Priorizar ejemplos donde se vea un criterio de zona remota, area de operacion o seleccion de rociadores directamente sobre el foco, y extraer la logica que se repite.

### Acceptance criteria

- [ ] Existen referencias reales suficientes para apoyar el criterio propuesto.
- [ ] Se identifican patrones de seleccion compatibles con incendios localizados.
- [ ] Se descartan ejemplos que actuen todos los rociadores de una planta sin justificacion tecnica.

---

## Phase 4: Definicion del criterio de seleccion

**User stories**: resolver que rociadores activar en la ultima planta de forma defendible.

### What to build

Definir un criterio principal: activar los rociadores que permitan cubrir aproximadamente `72 m^2` en la zona mas desfavorable de la ultima planta, priorizando la combinacion que represente mayor exigencia hidraulica razonable.

Si hay varias combinaciones posibles, elegir la que:

- quede mas alejada hidraulicamente;
- presente mayor perdida de presion;
- cubra la mayor superficie util de la vivienda dentro del area normativa;
- incluya el rociador mas desfavorable dentro de esa zona.

### Acceptance criteria

- [ ] Existe un criterio unico y reproducible para seleccionar los rociadores de simulacion.
- [ ] El criterio esta alineado con la norma, la guia de DMelect y la practica real encontrada.
- [ ] Se documenta que la activacion no equivale a encender todos los rociadores de la vivienda.

---

## Phase 5: Protocolo justificativo final

**User stories**: disponer de una respuesta final utilizable en la memoria o en la practica.

### What to build

Redactar un protocolo corto y trazable que explique:

- por que la ultima planta es la mas desfavorable;
- por que se usa el area normativa de `72 m^2`;
- que rociadores deben activarse en DMelect;
- como se justifica la eleccion frente a una activacion total de la planta;
- que limites tiene la hipotesis y cuando deberia revisarse.

El resultado debe servir como referencia para futuras simulaciones del proyecto.

### Acceptance criteria

- [ ] El protocolo responde de forma directa a la duda tecnica planteada.
- [ ] La justificacion normativa, operativa y practica queda separada y clara.
- [ ] El texto final permite repetir la decision sin ambiguedad.

## Test Plan

- Confirmar que el criterio final no activa mas superficie de la necesaria por hipotesis de incendio.
- Verificar que la seleccion de rociadores se puede reproducir en DMelect.
- Revisar que cada conclusion tenga respaldo en `PCI_Practicas`, `DMelect_Guide` o un caso real encontrado con Exa.
- Comprobar que el documento final no mezcla la duda de criterio con la ejecucion de la simulacion.

## Assumptions

- La clasificacion de partida es R01.
- El valor de referencia para el area de operacion es `72 m^2`, pendiente de confirmacion documental exacta si el cuaderno usa una formulacion distinta.
- El entregable esperado es un protocolo justificativo, no una simulacion ejecutada.
- La decision final debe priorizar un incendio localizado y la zona hidraulicamente mas desfavorable, no la activacion total de la planta.
