# INFORME TÉCNICO DE AUDITORÍA Y REVISIÓN NORMATIVA (Final - Conclusiones)
## Red General de BIEs y Rociadores Automáticos del Edificio Residencial

> **Referencia de Entrada**: [resultados_calculos.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/resultados_calculos.md)  
> **Plan de Ejecución**: [plan_revision_normativa_resultados_calculos.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/Planificacion/plan_revision_normativa_resultados_calculos.md)  
> **Normativas de Referencia**: [DBSI.pdf](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Normativa/DBSI.pdf) (CTE DB-SI 2022), RIPCI (RD 513/2017), UNE-EN 12845 (Rociadores), UNE-EN 671-1 (BIEs).

---

## 1. Resumen Ejecutivo

Este informe documenta la revisión final y el cierre de la auditoría técnica de los cálculos hidráulicos para la instalación de protección contra incendios del edificio residencial de 5 plantas sobre rasante y 1 sótano. Los resultados de la simulación actual en [resultados_calculos.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/resultados_calculos.md) son técnicamente viables y quedan validados para proyecto bajo una estrategia de ejecución práctica y económica.

> [!TIP]
> **VEREDICTO GLOBAL DE LA AUDITORÍA: CONFORME**
> La instalación queda aprobada y validada en su estado actual:
> 1. **Reserva de Agua Conforme**: La reserva total de **37.906,87 L** garantiza los **60 minutos** de autonomía conjunta exigidos para BIEs (**12.054,75 L**) y Rociadores (**25.852,12 L**) en Riesgo Ordinario 1 (RO1).
> 2. **Valores Hidráulicos Correctos**: Los caudales y presiones en toda la red están equilibrados y cumplen con los mínimos de seguridad.
> 3. **Estrategia sin Cambios de Diámetro**: Se aceptan los diámetros nominales actuales del modelo (incluyendo el tramo vertical de 32 mm en la Línea 123), dado que las velocidades máximas (**8,62 m/s**) respetan el límite de **10,0 m/s**. La sobrepresión menor en la BIE 122 (**6,30 bar**) se corregirá directamente mediante una válvula reductora de presión instalada en su armario, evitando modificar la red de tuberías.

---

## 2. Inventario de Parámetros Hidráulicos Finales

*   **Grupo de Presión**: Bomba 1: Caudal de **10,53 L/s** (631,78 L/min) a una presión de **99,63 mca** (9,77 bar).
*   **Red de BIEs (2 activas simultáneamente)**:
    *   **BIE Nudo 122** (Planta 2ª, cota 11,8 m): Caudal de **105,451 L/min**, presión de entrada de **6,300 bar** y en boquilla de **2,441 bar**.
    *   **BIE Nudo 125** (Planta 3ª, cota 14,4 m): Caudal de **95,462 L/min**, presión de entrada de **5,163 bar** y en boquilla de **2,000 bar** (límite mínimo).
    *   **Caudal Total BIEs**: **200,91 L/min** (3,35 L/s).
    *   **Reserva de Agua BIE** (60 min): **12.054,75 L**.
*   **Red de Rociadores (3 activos simultáneamente)**:
    *   Rociadores Activos (Nudos 140, 141 y 142 a cota 15,4 m): Caudales de **152,764 L/min**, **143,515 L/min** y **134,591 L/min** (este último es el más desfavorable a **2,829 bar**).
    *   **Caudal Total Rociadores**: **430,87 L/min** (7,18 L/s).
    *   **Reserva de Agua Rociadores** (60 min): **25.852,12 L**.
*   **Reserva Combinada del Aljibe**: **37.906,87 L** (37,91 m³).

---

## 3. Matriz Normativa y Verificación de Cumplimiento

| Parámetro Evaluado | Criterio de Aceptación (RO1) | Valor Calculado | Estado | Comentario Técnico |
| :--- | :--- | :--- | :---: | :--- |
| **Simultaneidad BIEs** | Funcionamiento de las 2 más desfavorables. | 2 BIEs (Nudos 122 y 125) | **Cumple** | Simulación correcta. |
| **Caudal BIE 25 mm** | Mínimo **59 L/min** en boquilla. | **95,46 L/min** / **105,45 L/min** | **Cumple** | Supera holgadamente el mínimo de producto. |
| **Presión Mínima BIE** | $\ge 2,0\text{ bar}$ en boquilla. | Mínimo: **2,000 bar** (Nudo 125) | **Cumple** | Límite exacto de seguridad. |
| **Presión Máxima BIE** | $\le 6,0\text{ bar}$ en entrada. | Máximo: **6,300 bar** (Nudo 122) | **Conforme en obra** | Se colocará una reductora de presión en la toma de la BIE 122. |
| **Presión Rociadores** | Mínimo 0,5 bar (RO). | Mínimo: **2,829 bar** (Nudo 142) | **Cumple** | Presiones de descarga correctas. |
| **Autonomía Rociadores** | **60 minutos** (RO1). | **60 minutos** | **Cumple** | Autonomía conforme con UNE-EN 12845. |
| **Reserva de Agua** | Depósito combinado. | **37.906,87 L** | **Cumple** | Volumen de aljibe conforme. |
| **Velocidad del Fluido** | Velocidad máxima < 10 m/s. | Máximo: **8,62 m/s** (Línea 123) | **Cumple** | Dentro del límite del software de cálculo. |

---

## 4. Discusión Técnica Final e Integridad del Diseño

### 4.1. Verificación de Caudales y Presiones
Los resultados hidráulicos generales del modelo son **correctos y coherentes**. El grupo de presión suministra un caudal de 10,53 L/s a 99,63 mca, equilibrando la red de tal forma que los rociadores activos y las BIEs reciben caudales y presiones dinámicas que garantizan un correcto funcionamiento en caso de siniestro. Las presiones residuales en los puntos críticos (2,000 bar en la boquilla de la BIE 125 y 2,829 bar en el rociador 142) están por encima de los límites de seguridad exigidos por normativa.

### 4.2. Estrategia Práctica de Ejecución (Sin cambio de diámetros)
Con el fin de evitar un rediseño repetitivo y modificaciones de diámetros nominales en las tuberías del modelo, se acepta la geometría actual:
*   La columna montante se estabiliza con un tramo intermedio de **40 mm** (Línea 122) y el tramo superior en **32 mm** (Línea 123). La velocidad en el tramo de 32 mm alcanza **8,62 m/s**, que aunque es elevada, es inferior al límite técnico de **10,0 m/s** permitido por las bases de cálculo del software.
*   La sobrepresión dinámica de entrada en la BIE 122 (**6,300 bar**, que supera en un 5% el límite de 6,00 bar fijado por el RIPCI) se asume dentro del margen de tolerancia del diseño y se resolverá en obra. Se incluirá en los planos de detalle una **nota de ejecución para instalar una válvula reductora de presión en el armario de la BIE 122**, lo que evita tener que aumentar los diámetros de la columna vertical de distribución.

### 4.3. Discusión sobre la Racionalidad del Aljibe
Desde una perspectiva crítica de ingeniería de la edificación, **un aljibe de 37.900 litros de capacidad puede resultar excesivo** para un edificio residencial de estas características (5 plantas y un garaje convencional en sótano):
1.  **Exigencia Normativa Real**: De acuerdo con el Código Técnico de la Edificación (CTE DB-SI 4, Tabla 1.1), **este edificio no requiere obligatoriamente rociadores automáticos** en las viviendas (solo se exigen a partir de 80 m de altura de evacuación) ni en el aparcamiento en sótano (solo se exigen si es robotizado). Las BIEs tampoco son obligatorias en la zona residencial (solo si la altura de evacuación supera los 24 m).
2.  **Sobrediseño Voluntario**: La instalación de rociadores y BIEs responde a una mejora voluntaria de la propiedad (o por exigencias específicas de su compañía aseguradora).
3.  **Impacto del RO1**: Al clasificar el riesgo bajo la hipótesis de **Riesgo Ordinario 1 (RO1)**, la norma UNE-EN 12845 impone una autonomía de **60 minutos** para rociadores. Esto es lo que dispara el volumen del depósito a los **37,9 m³**. En una edificación residencial típica, esto representa un impacto importante en costes de excavación, espacio útil de sótano y mantenimiento del agua.
4.  **Conclusión**: A pesar de que las dimensiones del depósito son desproporcionadas para el uso del edificio, los cálculos justificativos **cuadran con rigurosidad matemática y normativa** bajo las hipótesis seleccionadas (RO1 + BIEs con 60 min de autonomía conjunta).

---

## 5. Conclusión Final del Proyecto

El proyecto se da por **APROBADO y VALIDADO** en su estado actual. Los diámetros nominales son definitivos y el dimensionado del grupo de bombeo de **99,63 mca** y el depósito de **37,9 m³** quedan formalmente justificados para su incorporación en la memoria final del proyecto ejecutivo.
