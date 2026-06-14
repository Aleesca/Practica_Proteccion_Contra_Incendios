# Plan de Revisión: Cualificación de Resumen, Ecuaciones de Cálculo y Expansión de la Memoria

Este plan maestro define las fases y directrices de diseño para revisar y expandir la memoria técnica de protección contra incendios del edificio residencial en `Practica_PCI_LaTeX/main.tex`, utilizando como fuentes operativas primarias los Markdown en `Proyecto/Especificaciones/` y la orquestación a través de `task-orchestrator`.

---

## 1. Objetivos de la Revisión

1. **Cualificación del Resumen**: Eliminar todos los datos numéricos específicos del apartado *Resumen* (`00_resumen.md` y `main.tex`). Deberá presentarse una síntesis puramente cualitativa y conceptual centrándose en el alcance (BIEs y rociadores), la metodología por modelado tridimensional y la conclusión de viabilidad normativa del diseño global.
2. **Planteamiento de Ecuaciones Matemáticas**: Incorporar en *Resultados y discusión* las formulaciones hidráulicas que rigen las comprobaciones del modelo de cálculo, acompañadas de su correspondiente aplicación numérica explícita paso a paso para los puntos críticos desfavorables de la red.
3. **Reducción del Uso de Tablas**: Reemplazar o condensar las tablas masivas por prosa técnica detallada. Específicamente, se eliminará la tabla de parámetros de diseño en Metodología, y se simplificarán las tablas de verificación y comparativa en Resultados y Discusión.
4. **Redacción Extensiva**: Ampliar exhaustivamente la redacción de cada sección de la memoria para dotarla de mayor profundidad analítica, rigor y madurez en ingeniería de edificación.

---

## 2. Definición de Ecuaciones a Incorporar

Se incorporarán de forma explícita las siguientes formulaciones en la sección de Resultados y Discusión:

### A. Ecuación de Descarga de Consumos (Factor K)
Para comprobar el caudal dinámico de descarga de Bocas de Incendio Equipadas (BIE) y rociadores automáticos en base a la presión residual en el emisor:
$$Q = K \cdot \sqrt{P}$$
*   $Q$: Caudal de descarga del emisor ($\text{L/min}$).
*   $K$: Coeficiente de descarga adimensional propio del equipo ($K_{BIE} = 42$; $K_{roc} = 161,3$).
*   $P$: Presión residual dinámica en el nudo de descarga ($\text{bar}$).

### B. Ecuación de Hazen-Williams (Pérdidas de Carga Continuas)
Para justificar analíticamente las pérdidas por fricción lineales a lo largo de las tuberías de la instalación:
$$h_f = 10,67 \cdot L \cdot Q^{1,852} \cdot C^{-1,852} \cdot D^{-4,87}$$
*   $h_f$: Pérdidas de carga por rozamiento ($\text{mca}$).
*   $L$: Longitud del tramo de tubería ($\text{m}$).
*   $Q$: Caudal de paso por el tramo ($\text{m}^3/\text{s}$).
*   $C$: Coeficiente de rugosidad de Hazen-Williams ($C = 120$ para acero al carbono).
*   $D$: Diámetro interior del tubo ($\text{m}$).

### C. Ecuación de Pérdidas de Carga Totales (con Pérdidas Singulares)
$$h_{f, total} = h_f \cdot (1 + f_s)$$
*   $h_{f, total}$: Pérdidas de carga totales en el tramo ($\text{mca}$).
*   $f_s$: Coeficiente de incremento por accesorios de la red ($f_s = 0,20$, correspondiente al 20%).

### D. Ecuación de Velocidad del Fluido
Para la verificación física de que el agua circula por debajo del límite de erosión técnica ($10,0\text{ m/s}$):
$$v = \frac{4 \cdot Q}{\pi \cdot D^2}$$
*   $v$: Velocidad media del agua ($\text{m/s}$).
*   $Q$: Caudal volumétrico de paso por la sección ($\text{m}^3/\text{s}$).
*   $D$: Diámetro interior de la conducción ($\text{m}$).

### E. Ecuación de Reserva de Agua y Capacidad del Aljibe
Para la justificación de la autonomía requerida del depósito combinado de incendios:
$$V_{total} = \left( Q_{BIE, total} \cdot t_{BIE} \right) + \left( Q_{roc, total} \cdot t_{roc} \right)$$
*   $V_{total}$: Volumen mínimo útil de reserva ($\text{L}$).
*   $Q_{BIE, total}$: Caudal de descarga conjunto del escenario de BIEs ($Q_{BIE, total} = Q_{122} + Q_{125}$ en $\text{L/min}$).
*   $Q_{roc, total}$: Caudal de descarga conjunto del área de diseño de rociadores ($\sum_{i=140}^{142} Q_i$ en $\text{L/min}$).
*   $t_{BIE}$, $t_{roc}$: Tiempo mínimo de autonomía exigido por normativa ($60\text{ minutos}$ bajo RO1).

---

## 3. Estrategia de Reducción de Tablas y Ampliación de Prosa

### A. Metodología (`02_metodologia.md`)
*   **Acción**: **Eliminar completamente** la tabla `tab:parametros_diseno` (Parámetros de diseño y datos generales).
*   **Reemplazo**: Traducir toda la información paramétrica (rugosidades, método de pérdidas de carga, presiones mínimas de catálogo, clase de riesgo y autonomías) en prosa extensa en la subsección *Datos introducidos en el programa*. Se describirá detalladamente la base física de cada valor y su justificación técnica o normativa.

### B. Resultados y Discusión (`03_resultados_discusion.md`)
*   **Acción 1**: **Eliminar** o **reducir drásticamente** la tabla `tab:verificacion` (Matriz de verificación de cumplimiento).
*   **Reemplazo 1**: Explicar pormenorizadamente cada criterio en párrafos narrativos estructurados. Se analizarán las condiciones de velocidad máxima de paso por columnas, justificación pormenorizada del estado de las BIEs y la resolución de la sobrepresión de la BIE 122 mediante la válvula reductora.
*   **Acción 2**: **Eliminar completamente** la tabla `tab:comparativa_riesgos` (Comparativa RO1 vs RL).
*   **Reemplazo 2**: Traducir la comparativa de diseño a un desarrollo textual exhaustivo de la "Paradoja del Riesgo Ligero". Se discutirá de manera amplia y fluida cómo el aumento de rociadores activos y la mayor presión de ficha en RL elevan la potencia del bombeo a pesar de reducir el depósito de reserva de agua por la rebaja de autonomía.

---

## 4. Secuencia de Activación Secuencial

El flujo documental se gobernará secuencialmente, bloqueando modificaciones directas a LaTeX hasta que todos los Markdown de especificación estén cerrados y validados.

### Fase 1. Modificar `00_resumen.md`
*   **Entrada**: `Proyecto/Especificaciones/00_resumen.md`.
*   **Cambio**: Redactar un resumen puramente cualitativo, eliminando el caudal de bomba, la altura de la bomba, el volumen del aljibe y las presiones residuales de los nudos desfavorables.
*   **Control**: Mantener una extensión inferior a 250 palabras en prosa formal y sin listas.

### Fase 2. Expandir `01_introduccion_objetivos.md`
*   **Entrada**: `Proyecto/Especificaciones/01_introduccion_objetivos.md`.
*   **Cambio**: Ampliar la redacción en la introducción histórica y contextual sobre la protección activa y la justificación de los sistemas de BIEs y rociadores.

### Fase 3. Revisar y Expandir `02_metodologia.md` (Sin Tablas)
*   **Entrada**: `Proyecto/Especificaciones/02_metodologia.md`.
*   **Cambio**: Eliminar la tabla `tab:parametros_diseno`. Convertir los parámetros en prosa analítica detallada. Describir la topología de la columna montante vertical común y justificar exhaustivamente el trazado.

### Fase 4. Revisar y Expandir `03_resultados_discusion.md` (Ecuaciones y Sin Tablas)
*   **Entrada**: `Proyecto/Especificaciones/03_resultados_discusion.md` y `Proyecto/resultados_calculos.md`.
*   **Cambio**:
    1.  Introducir las ecuaciones matemáticas de caudal, velocidad, pérdidas de carga (Hazen-Williams) y volumen de aljibe.
    2.  Presentar los cálculos numéricos paso a paso para el rociador crítico (Nudo 142) y la BIE crítica (Nudo 125), demostrando explícitamente cómo la presión residual determina el caudal.
    3.  Eliminar la tabla de matriz de verificación y la tabla comparativa de riesgos, sustituyéndolas por redacción técnica y explicativa.
    4.  Analizar detalladamente el efecto del coeficiente de incremento del 20% en accesorios.

### Fase 5. Expandir `04_conclusiones.md`
*   **Entrada**: `Proyecto/Especificaciones/04_conclusiones.md`.
*   **Cambio**: Incrementar la prosa técnica argumentando con mayor madurez las implicaciones de las decisiones de diseño adoptadas (reductora de presión e hipótesis de RO1 voluntaria).

### Fase 6. Consolidación Global en LaTeX
*   **Entrada**: Archivos `.md` de especificaciones cerrados y `Practica_PCI_LaTeX/main.tex`.
*   **Cambio**: Invocar a `latex-writer` para consolidar los cambios en `main.tex`.

### Fase 7. Compilación y Validación Final
*   **Entrada**: `Practica_PCI_LaTeX/main.tex` consolidado.
*   **Cambio**: Invocar a `latex-validator` para compilar y certificar la ausencia de incidencias estáticas y dinámicas.

---

## 5. Criterios de Aceptación de la Revisión

- El resumen **no contiene cifras** de caudal, altura, volumen ni presiones en nudos.
- Resultados y Discusión **plantea explícitamente** las fórmulas de descarga ($Q=K\sqrt{P}$), Hazen-Williams ($h_f$), velocidad ($v$) y volumen ($V$), mostrando el cálculo paso a paso.
- Se han **eliminado** la tabla de parámetros de diseño (`tab:parametros_diseno`) y la tabla comparativa de riesgos (`tab:comparativa_riesgos`). La tabla de verificación (`tab:verificacion`) ha sido reducida o eliminada.
- Todos los apartados muestran una redacción **claramente más extensiva y detallada** que la versión previa.
- La compilación final en LaTeX del archivo `main.tex` finaliza correctamente y el PDF resultante se genera sin errores.
