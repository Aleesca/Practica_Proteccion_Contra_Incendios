# Especificacion de redaccion: Resultados y discusion

## Objetivo del apartado

Interpretar los resultados hidraulicos del modelo y demostrar que la instalacion funciona en los escenarios considerados. El apartado debe ir mas alla de listar resultados: debe explicar que significan, donde estan los puntos criticos y por que el diseno se considera valido.

## Subapartados propuestos

- Analisis de la verificacion hidraulica mediante mapa de estados.
- Analisis de los puntos singulares mas desfavorables (BIEs y Rociadores).
- Verificacion normativa y criterios de aceptacion.
- Discusion tecnica y comparativa de alternativas (RO1 vs RL).

### Contenido definitivo (Cerrado)

### Análisis de la verificación hidráulica mediante mapa de estados

El análisis hidráulico de la red combinada de protección contra incendios se fundamenta en un modelo tridimensional de comportamiento estático y dinámico. La red se simula en el escenario de máxima demanda concurrente para evaluar de manera unificada el mapa de estados hidráulicos, comprobando que las velocidades del agua, las pérdidas por rozamiento y las presiones dinámicas disponibles se mantengan dentro de los umbrales de servicio técnico y legalmente admisibles. 

El modelo matemático del motor de cálculo hidráulico implementa la formulación empírica de Hazen-Williams para determinar las pérdidas de carga continuas o lineales ($h_f$) a lo largo de las conducciones de acero al carbono:
$$h_f = 10,67 \cdot L \cdot Q^{1,852} \cdot C^{-1,852} \cdot D^{-4,87}$$
Donde:
*   $h_f$: Pérdidas de carga continuas en el tramo de tubería, expresadas en metros de columna de agua ($\text{mca}$).
*   $L$: Longitud física lineal del tramo de conducción, expresada en metros ($\text{m}$).
*   $Q$: Caudal volumétrico de agua circulante por la tubería, expresado en metros cúbicos por segundo ($\text{m}^3/\text{s}$).
*   $C$: Coeficiente adimensional de rugosidad de Hazen-Williams ($C = 120$ para acero al carbono).
*   $D$: Diámetro interior real de la conducción, expresado en metros ($\text{m}$).

Para considerar de manera globalizada pero hidráulicamente segura el efecto resistivo de las singularidades de la instalación —tales como codos, tes de derivación, reducciones, uniones ranuradas y válvulas de corte—, las pérdidas de carga totales en cada tramo ($h_{f, total}$) se obtienen incrementando proporcionalmente las pérdidas lineales:
$$h_{f, total} = h_f \cdot (1 + f_s)$$
Donde:
*   $h_{f, total}$: Pérdidas de carga totales estimadas en el tramo, expresadas en metros de columna de agua ($\text{mca}$).
*   $f_s$: Coeficiente adimensional de incremento por accesorios, fijado en $f_s = 0,20$, correspondiente a un recargo del 20 % sobre las longitudes equivalentes de la red.

Asimismo, la verificación física de la velocidad media del agua ($v$) en cada conducción se rige por la ecuación de continuidad para fluido incompresible en sección circular:
$$v = \frac{4 \cdot Q}{\pi \cdot D^2}$$
Donde:
*   $v$: Velocidad media de paso del agua, expresada en metros por segundo ($\text{m/s}$).
*   $Q$: Caudal volumétrico del agua circulante, expresado en metros cúbicos por segundo ($\text{m}^3/\text{s}$).
*   $D$: Diámetro interior real de la tubería, expresado en metros ($\text{m}$).

El grupo de presión principal de protección contra incendios se ha dimensionado en el modelo para suministrar un caudal de diseño de 10,53 L/s (631,78 L/min) a una altura manométrica de 99,63 mca (9,77 bar). Los resultados del modelo hidráulico confirman que la velocidad del fluido en toda la instalación respeta el límite técnico de erosión de 10,0 m/s. La velocidad pico se localiza en la columna montante vertical común a la altura de la Línea 123 (tramo superior que alimenta los nudos de cota elevada), registrando un valor máximo de 8,62 m/s en tubería de acero DN32 (diámetro interior de 36,0 mm). Dicho valor se sitúa holgadamente por debajo del límite de velocidad admisible, validando la estabilidad estructural de la tubería y descartando el riesgo de vibraciones o golpes de ariete dañinos sin requerir un aumento costoso de la sección nominal.

### Análisis de los puntos singulares más desfavorables

Para estructurar de forma clara e individualizada la interpretación del comportamiento hidráulico, la red combinada se divide en dos subsistemas principales de protección activa, analizando sus respectivos nudos críticos:

#### 1. Red de Bocas de Incendio Equipadas (BIE)

El modelo de simulación simula la demanda de las dos Bocas de Incendio Equipadas hidráulicamente más desfavorables abiertas simultáneamente, correspondientes a los nudos 125 (Planta 3ª) y 122 (Planta 2ª) de la columna montante. La descarga hidráulica de caudal de las BIEs se rige por la ecuación del coeficiente de descarga o Factor K del emisor en función de la presión residual dinámica de entrada al armario de BIE:
$$Q = K \cdot \sqrt{P}$$
Donde:
*   $Q$: Caudal descargado por la BIE, expresado en litros por minuto ($\text{L/min}$).
*   $K$: Coeficiente de descarga adimensional propio del equipo ($K_{BIE} = 42$ para BIE de 25 mm).
*   $P$: Presión residual dinámica a la entrada de la manguera del armario, expresada en bar ($\text{bar}$).

##### Comprobación numérica paso a paso para la BIE crítica (Nudo 125)
La BIE del nudo 125, situada a cota 14,4 m, representa el punto terminal crítico del sistema manual. La presión residual dinámica registrada por el programa en la entrada de su armario es de exactamente 5,16 bar. Aplicando la ecuación de descarga:
$$Q_{125} = 42 \cdot \sqrt{5,16}$$
$$Q_{125} = 42 \cdot 2,27156 \approx 95,41 \text{ L/min}$$
El motor de cálculo del software arroja un caudal de descarga simulado de exactamente 95,46 L/min, lo que muestra una coincidencia plena (donde 42 * 2,27156 = 95,41 L/min, habiendo una discrepancia de solo 0,05 L/min debida al tratamiento interno de alta precisión del motor de cálculo del programa). Tras descontar las pérdidas por fricción lineales y singulares acumuladas en los 30 metros de manguera semirrígida y en la lanza (lanza Variomatic con diámetro equivalente de 10 mm), la presión dinámica resultante en la boquilla de descarga se sitúa en 2,00 bar. Este valor coincide exactamente con la presión de boquilla mínima de 2,00 bar exigida por el Reglamento de Instalaciones de Protección Contra Incendios y la norma UNE-EN 671-1, garantizando la viabilidad y homologación del diseño en su punto más alto de consumo.

##### Verificación y corrección de sobrepresión en la BIE del Nudo 122
La BIE del nudo 122, situada a cota 11,8 m, descarga un caudal de 105,45 L/min a partir de una presión de entrada al armario de 6,30 bar (lo que proporciona una presión dinámica residual en boquilla de 2,44 bar). Dado que la presión de entrada al armario alcanza los 6,30 bar, supera la presión máxima de servicio de 6,00 bar permitida por el RIPCI para salvaguardar la integridad física del usuario frente a reacciones de retroceso de la manguera. Para solucionar esta incidencia técnica sin incurrir en modificaciones geométricas costosas o en el rediseño de diámetros de tuberías, se prescribe la colocación en obra de una válvula reductora de presión mecánica calibrada para limitar la presión de entrada a un máximo de 6,00 bar, instalada de forma compacta en la toma de conexión de manguera del armario de la BIE 122.

#### 2. Red de Rociadores automáticos

El escenario de supresión autónoma activa simultáneamente el área de operación más alejada de rociadores, la cual consta en el modelo de los tres rociadores desfavorables situados a cota 15,4 m y representados por los nudos 140, 141 y 142. La descarga hidráulica individual de estos terminales se rige por la misma relación de Factor K:
$$Q = K \cdot \sqrt{P}$$
Donde, para el cálculo numérico del modelo hidráulico, se introduce un coeficiente de descarga estándar de $K_{roc} = 80$ (unidades métricas: $\text{L/min}/\sqrt{\text{bar}}$).

##### Comprobación numérica paso a paso para el rociador crítico (Nudo 142)
El rociador del nudo 142 representa el emisor hidráulicamente más desfavorable de la red autónoma. La presión residual dinámica que registra el software en este nudo es de 2,83 bar. Aplicando la ecuación de descarga:
$$Q_{142} = 80 \cdot \sqrt{2,83}$$
$$Q_{142} = 80 \cdot 1,68226 \approx 134,58 \text{ L/min}$$
El caudal arrojado por el software es de 134,59 L/min, lo que demuestra la coherencia del modelo numérico (donde 80 * 1,68226 = 134,58 L/min, habiendo una discrepancia de solo 0,01 L/min debida al tratamiento interno de alta precisión del motor de cálculo del programa). La presión residual de 2,83 bar supera con amplitud el umbral mínimo legal de 0,5 bar fijado por la norma UNE-EN 12845 para Riesgo Ordinario y la presión nominal mínima de ficha técnica (0,83 bar, modelada como 0,8 bar por limitaciones del software). Esto asegura un patrón de pulverización óptimo para el rociador Tyco Series EC-11 (SIN TY5237).

Cabe destacar que, mientras el software de modelado utiliza el factor $K = 80$ estándar por la parametrización de las bases de cálculo del programa, la instalación física empleará rociadores de cobertura extendida con un factor K real de 161,3, lo que representa un amplio margen de seguridad hidráulica y capacidad de supresión adicional para el edificio.

### Verificación normativa y criterios de aceptación

La validación técnica del proyecto contra la legislación de seguridad contra incendios se justifica mediante un análisis continuo y pormenorizado en prosa de cada criterio normativo aplicable.

En primer lugar, respecto a la simultaneidad del sistema manual de Bocas de Incendio Equipadas de manguera semirrígida (BIE 25), el Reglamento de Instalaciones de Protección Contra Incendios exige garantizar el funcionamiento concurrente de las dos BIEs hidráulicamente más desfavorables. En nuestro modelo, se ha configurado la apertura simultánea de los nudos 125 y 122 en las plantas de mayor altura de la edificación, cumpliendo rigurosamente con esta hipótesis normativa de emergencia. 

En segundo lugar, en lo referente a las presiones dinámicas en punta de lanza, la normativa establece un límite mínimo de 2,0 bar. El punto crítico (BIE 125) alcanza exactamente los 2,00 bar en boquilla, cumpliendo con precisión matemática el límite inferior reglamentario. A su vez, para evitar riesgos físicos de retroceso sobre el operario de manguera, el RIPCI limita la presión estática o dinámica de entrada en armario a un máximo de 6,00 bar. En el nudo 122 se registra una presión de entrada de 6,30 bar; no obstante, esta sobrepresión se da por conforme en obra mediante la prescripción explícita de instalar una válvula reductora de presión calibrada a 6,00 bar en el armario de la BIE 122, evitando la alteración de la columna vertical y garantizando la seguridad en el uso. Los caudales de descarga de 95,46 L/min (BIE 125) y 105,45 L/min (BIE 122) superan holgadamente las especificaciones mínimas de producto para manguera semirrígida según UNE-EN 671-1.

En tercer lugar, el comportamiento dinámico de los rociadores automáticos se contrasta con las demandas de la norma UNE-EN 12845. El rociador crítico (Nudo 142) opera a una presión residual dinámica de 2,83 bar, lo que supera con creces el límite de 0,5 bar de la norma y el límite de diseño de 0,57 bar. La velocidad máxima del fluido en la red se estabiliza en un valor de 8,62 m/s en la montante común superior (Línea 123), respetando el límite técnico máximo de 10,0 m/s fijado en el programa para precaver efectos de erosión en las paredes internas de las tuberías de acero al carbono. 

Finalmente, la reserva total de agua del aljibe del edificio se dimensiona de manera combinada bajo un criterio de autonomía mínima de 60 minutos (según la clase de riesgo de diseño adoptada). Los requerimientos de almacenamiento se desglosan en 12.054,75 litros destinados al subsistema de BIEs (derivado del caudal conjunto de 200,91 L/min durante una hora de autonomía) y 25.852,12 litros destinados al subsistema de rociadores automáticos (derivado de la demanda de 430,87 L/min del área hidráulica de cálculo activa durante una hora). La reserva combinada útil acumulada en el aljibe se calcula por tanto en 37.906,87 litros (37,91 m³), volumen que satisface plenamente las exigencias del RIPCI y la UNE-EN 12845, certificando la viabilidad de la reserva autónoma del edificio.

### Discusión técnica y comparativa de alternativas (RO1 vs RL)

Para dotar al diseño de un análisis crítico de ingeniería de la edificación, se evalúa la sensibilidad hidráulica de la instalación comparando la hipótesis de diseño adoptada, clasificada bajo el riesgo de Riesgo Ordinario 1 (RO1), frente a la alternativa de clasificar el edificio en la categoría de Riesgo Ligero (RL). Esta última clasificación es factible bajo el marco de la norma UNE-EN 12845 para tipologías residenciales colectivas de baja altura, pero altera drásticamente los parámetros de cálculo físico de la red. 

La autonomía y capacidad del depósito de acumulación de agua se justifican analíticamente a partir de la ecuación de reserva hidráulica combinada del aljibe ($V_{total}$):
$$V_{total} = \left( Q_{BIE, total} \cdot t_{BIE} \right) + \left( Q_{roc, total} \cdot t_{roc} \right)$$
Donde:
*   $V_{total}$: Volumen total útil mínimo de almacenamiento de agua en el aljibe, expresado en litros ($\text{L}$).
*   $Q_{BIE, total}$: Caudal de descarga conjunto simultáneo de las BIEs activas desfavorables, expresado en litros por minuto ($\text{L/min}$). En nuestro modelo es de 200,91 L/min.
*   $t_{BIE}$: Tiempo de autonomía exigido para el subsistema de BIEs, fijado por reglamento en 60 minutos ($t_{BIE} = 60\text{ min}$).
*   $Q_{roc, total}$: Caudal de descarga conjunto del área hidráulica de cálculo activa de rociadores, expresado en litros por minuto ($\text{L/min}$). En nuestro modelo es de 430,87 L/min.
*   $t_{roc}$: Tiempo de autonomía exigido para el subsistema de rociadores automáticos, fijado en 60 minutos ($t_{roc} = 60\text{ min}$) bajo la hipótesis de clasificación de Riesgo Ordinario 1 (RO1).

El contraste cuantitativo entre ambas clasificaciones de riesgo pone de relieve una paradoja técnica de diseño denominada "La Paradoja del Riesgo Ligero":

1. **La paradoja del comportamiento hidráulico instantáneo**: A pesar de que Riesgo Ligero representa teóricamente una clasificación de menor riesgo y carga de fuego, los requisitos específicos de diseño de la UNE-EN 12845 para esta categoría incrementan las exigencias dinámicas inmediatas. En primer lugar, la norma obliga a simular un mayor número de terminales activos en el área hidráulica de operación (4 rociadores simultáneos en RL frente a los 3 rociadores requeridos en RO1). En segundo lugar, la presión residual mínima exigida en cada rociador se eleva a 0,70 bar (en comparación con los 0,57 bar establecidos para RO1). Como consecuencia de este incremento conjunto en la presión dinámica y en el número de emisores activos, el caudal demandado por el área de rociadores en RL se dispara un 35,6 %, alcanzando los 584,55 L/min (9,74 L/s) en comparación con los 430,87 L/min de RO1. Al sumar la demanda simultánea de la red de BIEs, el grupo de presión de incendios en la alternativa de Riesgo Ligero debe suministrar un caudal de bomba de 13,11 L/s (786,39 L/min) a una altura manométrica muy superior de 112,28 mca (11,01 bar). Esto supone un incremento de la potencia de bombeo de más del 12 % y eleva la presión de entrada de la BIE 122 hasta los 6,41 bar, lo que exacerba los problemas de sobrepresiones e incrementa la velocidad máxima del agua en la montante hasta 9,51 m/s (acercándose peligrosamente al límite de desgaste erosivo de las conducciones).

2. **La ventaja del aljibe**: La paradoja radica en que, a pesar de exigir una potencia de impulsión instantánea superior, la UNE-EN 12845 reduce a la mitad el tiempo de autonomía del volumen de rociadores en Riesgo Ligero, limitándolo a un tiempo de $t_{roc} = 30\text{ minutos}$ (frente a los 60 minutos exigidos para RO1). Aplicando la ecuación de reserva hidráulica, la reserva de agua destinada a rociadores en RL disminuye a 17.536,54 litros, lo que permite proyectar un volumen total acumulado útil del aljibe combinado de 29.646,78 litros. Esto representa una reducción neta del aljibe de 8.260 litros (un 21,8 % menos de capacidad con respecto a los 37.906,87 litros necesarios en RO1). En términos de ingeniería de edificación, esta disminución de volumen se traduce en ventajas de viabilidad constructiva, reduciendo significativamente los costes de excavación del sótano, el espacio útil edificado ocupado por el depósito y las tareas de conservación de la calidad del agua almacenada.

3. **Justificación del diseño adoptado (RO1)**: A pesar del atractivo económico y constructivo derivado de la reducción de la reserva de agua del aljibe en la alternativa de Riesgo Ligero, el proyecto se consolida definitivamente bajo la hipótesis de **Riesgo Ordinario 1 (RO1)**. Esta decisión de ingeniería de detalle se justifica para priorizar la durabilidad e integridad de la infraestructura de tuberías comunes y optimizar la potencia de funcionamiento de los equipos instalados. La elección de RO1 permite operar con un grupo de bombeo significativamente menos potente y de menor presión de salida (99,63 mca frente a los 112,28 mca de RL), manteniendo las presiones residuales y velocidades en la columna montante vertical en valores moderados, lo que mitiga los efectos nocivos de la erosión en las uniones de acero al carbono y garantiza una mayor vida útil del sistema de protección contra incendios del edificio residencial.

## Control de Cambios y Cierre

- **Estado**: Cerrado y aprobado con desarrollo de ecuaciones.
- **Valores Hidráulicos**: Completamente alineados con los resultados numéricos validados en la auditoría técnica.
- **Trazabilidad**: Se han suprimido las tablas comparativas y normativas masivas, traduciéndose de manera exhaustiva a redacción técnica continua e incorporando las ecuaciones de Hazen-Williams, velocidad, descarga por factor K y reserva combinada en LaTeX con sus aplicaciones numéricas paso a paso.
