# Plan: Revision de Resultados de Calculos BIE

> Source PRD: solicitud de revision de `Proyecto/Anotaciones/resultados_calculos_BIE.md`

## Architectural decisions

Durable decisions that apply across all phases:

- **Fuente de resultados**: usar `resultados_calculos_BIE.md` como entrada primaria de valores calculados.
- **Fuentes tecnicas externas**: buscar con Exa manuales, documentacion o guias de DMELECT relacionadas con modulos de PCI, BIEs, redes hidraulicas, perdidas de carga y sentido de circulacion.
- **Fuente normativa**: consultar el cuaderno NotebookLM `PCI_Practicas` para contrastar requisitos de BIEs, caudales minimos, presiones, simultaneidad, criterios de aceptacion y referencias normativas.
- **Trazabilidad**: cada valor revisado debe quedar ligado a una fuente: resultado calculado, manual DMELECT, normativa o criterio fisico-hidraulico.
- **Resultado esperado**: informe de revision con tabla de valores, veredicto por parametro y lista de incidencias o confirmaciones.

---

## Phase 1: Inventario de Valores Calculados

**User stories**: identificar que datos deben revisarse antes de compararlos con normativa o manuales.

### What to build

Extraer de `resultados_calculos_BIE.md` todos los valores relevantes para la revision hidraulica: caudales, presiones, perdidas de carga, diametros, longitudes, nodos, BIE desfavorable, simultaneidad y cualquier valor con signo negativo o anomalo.

Organizar los datos en una tabla de revision con columnas para valor, unidad, ubicacion/nodo/tramo, interpretacion preliminar y estado pendiente de verificacion.

### Acceptance criteria

- [ ] Existe una tabla completa de parametros hidraulicos revisables.
- [ ] Los caudales negativos, nulos o sospechosos quedan marcados explicitamente.
- [ ] Las unidades quedan normalizadas o anotadas si no son claras.
- [ ] Se identifica que valores son resultados finales y cuales son valores intermedios.

---

## Phase 2: Contraste con Manuales DMELECT

**User stories**: comprobar si los resultados se interpretan correctamente segun la logica del software usado.

### What to build

Buscar con Exa documentacion de DMELECT sobre instalaciones PCI/BIE, redes hidraulicas, calculo de caudales, presiones, perdidas de carga, sentido de flujo y tratamiento de signos.

Extraer criterios de interpretacion: como representa DMELECT los caudales por tramo, si el signo puede indicar sentido contrario al definido, si existen casos validos de caudal negativo y como deben leerse los resultados.

### Acceptance criteria

- [ ] Se localizan y registran fuentes DMELECT pertinentes.
- [ ] Se documenta como interpretar signos positivos y negativos en caudales o perdidas.
- [ ] Se distingue entre "valor negativo fisicamente imposible" y "signo negativo por convencion de orientacion".
- [ ] Cada conclusion sobre DMELECT incluye referencia consultable.

---

## Phase 3: Verificacion Normativa en NotebookLM

**User stories**: confirmar si los resultados cumplen los requisitos aplicables a BIEs.

### What to build

Consultar el cuaderno NotebookLM `PCI_Practicas` para recuperar criterios normativos aplicables: caudal minimo exigible, presion minima/maxima, simultaneidad de BIEs, condiciones de la BIE mas desfavorable, criterios de dimensionado y cualquier referencia a UNE, RIPCI, CTE DB-SI u otra normativa incluida en el cuaderno.

Comparar cada valor calculado con el criterio normativo correspondiente.

### Acceptance criteria

- [ ] Cada requisito normativo usado queda citado desde el cuaderno.
- [ ] Los valores calculados se clasifican como cumple, no cumple o requiere interpretacion.
- [ ] Las discrepancias entre DMELECT, normativa y resultado calculado quedan separadas.
- [ ] Se identifican valores criticos para la validez del diseno.

---

## Phase 4: Analisis de Caudales Negativos

**User stories**: resolver especificamente si pueden existir caudales negativos y que significan.

### What to build

Analizar todos los caudales negativos detectados y clasificarlos en una de estas categorias:

- signo por convencion de sentido del tramo;
- inversion real del flujo respecto al sentido definido;
- error de modelado, conexion o definicion de demanda;
- resultado fisicamente incoherente;
- dato insuficiente para concluir.

Cruzar esta interpretacion con manuales DMELECT, criterios hidraulicos y normativa.

### Acceptance criteria

- [ ] Cada caudal negativo tiene una explicacion individual.
- [ ] Se indica si el valor absoluto del caudal es aceptable o no.
- [ ] Se concluye si el signo negativo invalida el calculo o solo cambia la interpretacion del sentido.
- [ ] Se proponen comprobaciones adicionales si hay indicios de error de modelado.

---

## Phase 5: Informe Final de Revision

**User stories**: entregar una conclusion clara y accionable.

### What to build

Redactar un informe de revision con:

- tabla resumen de parametros calculados;
- fuente de validacion usada para cada parametro;
- cumplimiento normativo;
- interpretacion de caudales negativos;
- incidencias detectadas;
- recomendaciones de correccion o verificacion adicional.

El informe debe permitir decidir si los resultados de BIE son aceptables para la practica o si deben recalcularse/modificarse.

### Acceptance criteria

- [ ] El informe separa hechos, interpretacion y conclusiones.
- [ ] Incluye una conclusion global: valido, valido con observaciones o no valido.
- [ ] Incluye una seccion especifica sobre caudales negativos.
- [ ] Todas las afirmaciones tecnicas relevantes tienen fuente o justificacion hidraulica.
- [ ] Las acciones recomendadas son concretas y verificables.

## Test Plan

- Revisar que todos los valores de `resultados_calculos_BIE.md` esten representados en la tabla de revision.
- Verificar que cada requisito normativo usado proviene del cuaderno `PCI_Practicas`.
- Confirmar que las fuentes DMELECT localizadas tratan directamente el calculo PCI/BIE o redes hidraulicas aplicables.
- Comprobar que ningun caudal negativo queda sin clasificar.
- Validar que las conclusiones distinguen entre incumplimiento normativo, interpretacion de software y posible error de modelado.

## Assumptions

- El archivo `resultados_calculos_BIE.md` contiene los resultados hidraulicos necesarios para revisar la instalacion BIE.
- El cuaderno `PCI_Practicas` contiene normativa o apuntes suficientes para contrastar los requisitos aplicables.
- Exa sera la via de busqueda para localizar documentacion DMELECT.
- La revision sera documental y tecnica; no modificara el modelo DMELECT ni recalculara la instalacion salvo que el informe recomiende hacerlo.
