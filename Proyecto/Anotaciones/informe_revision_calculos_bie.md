# INFORME DE REVISIÓN DE CÁLCULOS DE LA RED DE BIE

> **Origen**: Solicitud de revisión del archivo [resultados_calculos_BIE.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/Anotaciones/resultados_calculos_BIE.md)  
> **Plan de Referencia**: [plan_revision_resultados_calculos_bie.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/Planificacion/plan_revision_resultados_calculos_bie.md)

---

## 1. Inventario de Valores Calculados (Fase 1)

Se extraen los datos fundamentales del anexo de cálculos hidráulicos para su posterior contraste técnico y normativo.

### Tabla 1.1: Inventario de Parámetros Hidráulicos

| Parámetro | Valor Calculado | Unidad | Ubicación / Nodo / Tramo | Tipo de Dato | Estado de Verificación |
| :--- | :---: | :---: | :--- | :---: | :---: |
| **Caudal de descarga de la BIE** | 95,466 | l/min | Nudo 18 (BIE 25) | Final | Pendiente (Caudal bajo) |
| **Caudal del grupo de bombeo** | 1,5911 (95,47) | l/s (l/min) | Línea 7 (8 $\rightarrow$ 9) | Final | Pendiente (Simultaneidad = 1) |
| **Presión en punta de lanza** | 2,0 | bar | Nudo 18 ($P_{boquilla}$) | Final | Conforme (Diseño base) |
| **Presión dinámica de entrada** | 5,163 | bar | Nudo 18 ($P_{dinam}$) | Intermedio | Conforme (Dentro de límites) |
| **Pérdida de carga de la bomba** | -69,34 | mca | Línea 7 (Bomba 8 $\rightarrow$ 9) | Intermedio | Conforme (Ganancia de energía) |
| **Caudal en tramo de subida (Riser)** | 1,5911 | l/s | Líneas 6, 15, 18, 17, 16, 13, 14 | Intermedio | Conforme (Línea en serie) |
| **Caudal en tramo de subida invertido** | -1,5911 | l/s | Línea 13 (19 $\rightarrow$ 17) | Intermedio | Anómalo (Signo negativo) |
| **Caudal de suministro del depósito** | -1,591 | l/s | Nudo 8 (Cota 0) | Intermedio | Anómalo (Signo negativo) |
| **Velocidad máxima en red** | 1,56 | m/s | Línea 8 (9 $\rightarrow$ 10) | Intermedio | Conforme (Límite max: 10 m/s) |
| **Pérdida de carga lineal máxima** | 0,487 | mca | Línea 13 (19 $\rightarrow$ 17) | Intermedio | Conforme (Con 20% secundario) |
| **Diámetro interior de tuberías** | 36,0 | mm | Dn 32 (Acero, C=120) | Intermedio | Conforme |
| **Reserva de agua calculada** | 5.727,96 | litros | General (Instalación) | Final | **No conforme** (Insuficiente) |
| **Número de BIEs simultáneas** | 1 | ud | Nudo 18 activo | Final | **No conforme** (Falta BIE 2) |

---

## 2. Contraste con Manuales DMELECT (Fase 2)

A partir de la consulta del manual técnico de edificaciones de DMELECT (`Manual_edificios_DMELECT.pdf`), se extraen las siguientes reglas de diseño y de funcionamiento interno del software:

### 2.1. Sentido de Circulación y Convención de Dibujo
* **Establecimiento del Flujo**: En los programas de cálculo hidráulico de DMELECT, el sentido del flujo no se define de forma analítica en el cálculo, sino de manera **topológica** durante el dibujo.
* **Nudo Origen**: La instalación debe comenzar obligatoriamente en un nudo de suministro (depósito, acometida o grupo de bombeo). Las tuberías deben trazarse aguas abajo desde la alimentación hacia los consumos.
* **Trazado Inverso**: Si una tubería se traza "aguas arriba" (desde el punto de consumo hacia la alimentación), el software calcula correctamente la magnitud física, pero el vector de la tubería queda opuesto al sentido real del flujo. Esto resulta en la visualización de un **caudal negativo** ($Q < 0$) en los listados técnicos.

### 2.2. Pérdidas de Carga Negativas en Grupos de Bombeo
* En los listados de DMELECT, el término de pérdidas de carga ($hf$) para elementos activos como las bombas se muestra con **signo negativo ($-$)**.
* Esto no representa un error, sino una **ganancia de energía (altura manométrica)** aportada al fluido por el grupo de presión para contrarrestar el desnivel geométrico y las pérdidas por fricción en las tuberías.

### 2.3. Problemas de Continuidad por Solapes
* El manual advierte del error común de solapar nudos verticalmente sin utilizar la función **"Enlace"** de la barra de herramientas. Si dos nudos se superponen sin conexión física real, el software genera un circuito abierto (red rota), lo que impide que el motor hidráulico distribuya los caudales.

---

## 3. Verificación Normativa en NotebookLM (Fase 3)

Consultando el cuaderno `PCI_Practicas` (especialmente el documento de la *Guía Técnica de Aplicación del RIPCI*, RD 513/2017), se contrastan los requisitos normativos para BIEs de 25 mm:

### Tabla 3.1: Matriz de Cumplimiento Normativo

| Parámetro | Requisito Normativo (RIPCI / UNE-EN 671-1) | Valor Calculado | Estado | Discrepancia / Comentario |
| :--- | :--- | :---: | :---: | :--- |
| **Caudal mínimo** | Entorno a **100 l/min** (1,67 l/s) por BIE 25. | 95,47 l/min | **Requiere Interpretación** | Es ligeramente inferior al valor guía de 100 l/min (-4.5%), pero cumple formalmente al garantizar una presión de boquilla mínima de 2 bar con un factor K=42 ($Q = 42 \cdot \sqrt{P}$). |
| **Presión en punta de lanza** | Mínimo **2 bar** ($P_{boquilla}$) dinámica. | 2,0 bar | **Cumple** | Cumple con el mínimo dinámico en punta de lanza. |
| **Presión dinámica a la entrada** | Entre **3,0 bar y 6,0 bar** ($300\text{ kPa} - 600\text{ kPa}$). | 5,163 bar | **Cumple** | La presión en la entrada de la BIE 18 (5,16 bar) se sitúa correctamente en el rango normativo. |
| **Simultaneidad de BIEs** | **2 BIEs** simultáneas en la situación más desfavorable. | 1 BIE | **No Cumple** | Solo se ha configurado el funcionamiento de 1 BIE (Nudo 18). Se omitió la segunda BIE. |
| **Autonomía del sistema** | Mínimo **1 hora** (60 minutos) de funcionamiento. | 60 min | **Cumple** | El diseño de autonomía temporal es el correcto (60 min). |
| **Reserva de agua para BIEs** | $2\text{ BIEs} \times 100\text{ l/min} \times 60\text{ min} = \mathbf{12.000\text{ litros}}$ ($12\text{ m}^3$). | 5.727,96 l | **No Cumple** | La reserva es de solo $5.728\text{ litros}$, lo cual corresponde a **1 sola BIE** en funcionamiento. Falta el 52% del volumen requerido. |
| **Velocidad máxima** | Límite del diseño: **10 m/s** (práctica usual: $< 2.5 - 5\text{ m/s}$). | 1,56 m/s | **Cumple** | Velocidad hidráulicamente muy conservadora y segura. |

---

## 4. Análisis de Caudales y Signos Negativos (Fase 4)

Se realiza un diagnóstico individualizado de los valores con signo negativo o anomalías numéricas detectadas en los resultados:

### 4.1. Línea 13 (Nudo 19 $\rightarrow$ Nudo 17): Caudal = -1,5911 l/s
* **Naturaleza física**: El caudal circula físicamente en sentido ascendente desde el nudo 17 ($z = 12,9\text{ m}$) hacia el nudo 19 ($z = 14,4\text{ m}$).
* **Explicación del signo**: Al dibujar en DMELECT, la tubería se definió con el nudo 19 como origen y el nudo 17 como destino. Al ser el flujo real opuesto a la dirección del dibujo (ascendente frente a vector descendente del tramo), el programa muestra el caudal con signo negativo.
* **Veredicto**: **Válido instrumentalmente**. El valor absoluto ($1,5911\text{ l/s}$) es correcto y el signo es meramente una convención de representación gráfica de DMELECT. No invalida la física del cálculo.

### 4.2. Nudo 8 (Cota 0): Caudal = -1,591 l/s
* **Naturaleza física**: Este es el nudo de aspiración del grupo de bombeo, que conecta con el depósito de almacenamiento de agua.
* **Explicación del signo**: DMELECT emplea el signo negativo para los caudales en los nudos para indicar **entradas de caudal al sistema** (fuentes/aportes), mientras que los signos positivos denotan consumos/salidas (como el nudo 18 de la BIE activa).
* **Veredicto**: **Válido**. Sigue estrictamente la convención de signos del motor hidráulico del software.

### 4.3. Línea 7 (Bomba 8 $\rightarrow$ 9): Pérdida de carga = -69,34 mca
* **Naturaleza física**: Aporte de energía del grupo de presión de incendios.
* **Explicación del signo**: Una bomba introduce energía al sistema en lugar de disiparla. Al resolver la ecuación de energía:
  $$H_1 - H_2 = h_f$$
  Para la bomba, la pérdida de carga resulta negativa ($hf = -69,34\text{ mca}$), lo que físicamente equivale a una altura manométrica de bombeo de $69,34\text{ mca}$ (aproximadamente $6,8\text{ bar}$).
* **Veredicto**: **Válido y correcto**. Representa la altura de bombeo necesaria para alimentar la red.

---

## 5. Incidencias Críticas y Errores de Modelado (Fase 5)

Durante la auditoría técnica detallada de los resultados, se han identificado las siguientes incidencias críticas que comprometen la validez del cálculo:

### 5.1. Incidencia de Simultaneidad y Reserva de Agua (Crítica)
El sistema ha sido calculado abriendo únicamente la BIE en el nudo 18 (última planta).
* **Problema**: El RIPCI exige el cálculo con las **dos BIEs más desfavorables abiertas simultáneamente** (por ejemplo, nudos 18 y 15).
* **Impacto**:
  1. El caudal circulante por la montante vertical (riser) principal debe ser el doble ($2 \times 1,5911\text{ l/s} \approx 3,18\text{ l/s}$).
  2. Al circular el doble de caudal, las pérdidas de carga en la tubería vertical aumentarán por un factor de $2^{1,852} \approx 3,61$.
  3. El grupo de presión de $69,34\text{ mca}$ calculado para $1,59\text{ l/s}$ será **insuficiente** para abastecer a ambas BIEs simultáneamente con las presiones y caudales requeridos.
  4. El volumen del depósito de reserva contra incendios ($5.728\text{ litros}$) se calculó para 1 sola BIE durante 60 minutos. Normativamente se requiere una reserva mínima de **12.000 litros** (2 BIEs $\times$ 100 l/min $\times$ 60 min). El volumen actual es un **52% inferior al mínimo legal**.

### 5.2. Duplicidad y Colisión en la Numeración de Nudos (Grave)
Se observa una grave falta de coherencia en la designación de nudos dentro de las tablas de resultados de DMELECT:
* **Nudos duplicados**:
  * **Nudo 8**: Se usa para la aspiración del depósito (Cota 0m) y para un nudo de la tubería vertical en planta 2 (Cota 5.1m).
  * **Nudo 9**: Se usa para la descarga de la bomba (Cota 0m) y para la BIE de la planta 2 (Cota 6.6m).
  * **Nudo 11**: Se usa para el nudo de planta baja (Cota 0m) y para un nudo de tubería vertical en planta 3 (Cota 7.7m).
  * **Nudo 12**: Se usa para la BIE de planta 1 (Cota 4.0m) y para la BIE de planta 3 (Cota 9.2m).
  * **Nudo 14**: Se usa para el nudo vertical en planta 1 (Cota 4.0m) y en planta 4 (Cota 10.3m).
* **Impacto**: Esta colisión de identificadores en el software puede inducir a errores en la lectura de resultados, dificulta las comprobaciones de mantenimiento y la trazabilidad de los tramos, y denota un modelado gráfico deficiente.

---

## 6. Recomendaciones de Corrección y Conclusiones

> [!CAUTION]
> **VEREDICTO GLOBAL DEL CÁLCULO: NO VÁLIDO (Requiere corrección y recálculo)**

Los resultados actuales del anexo de cálculos **no cumplen** con las exigencias legales del RIPCI (RD 513/2017) ni con los principios de diseño hidráulico seguro. Se recomienda aplicar de forma inmediata las siguientes correcciones en el modelo de DMELECT:

1. **Corrección de Simultaneidad (Obligatorio)**:
   * Activar y abrir de forma simultánea los dos nudos de BIE hidráulicamente más desfavorables del edificio: **Nudo 18** (planta superior, cota 14.4) y **Nudo 15** (planta inferior inmediata, cota 11.8).
   * Volver a ejecutar el cálculo hidráulico.

2. **Rediseño del Depósito y Reserva de Agua (Obligatorio)**:
   * Incrementar la reserva de agua de protección contra incendios del edificio a un mínimo de **12.000 litros** reales de capacidad útil, para garantizar 1 hora de autonomía de dos BIEs.

3. **Renumeración de la Red (Recomendado)**:
   * Cambiar las etiquetas de los nudos en el programa antes del recálculo para eliminar la duplicidad de números. Se sugiere utilizar prefijos de planta:
     * Planta baja (Cotas 0 - 2.5m): Nudos 10, 11, etc.
     * Planta 1 (Cotas 4m): Nudos 101, 102, 103...
     * Planta 2 (Cotas 5.1m - 6.6m): Nudos 201, 202, 203...
     * Planta 3 (Cotas 7.7m - 9.2m): Nudos 301, 302, 303...
     * Planta 4 (Cota 10.3m - 11.8m): Nudos 401, 402, 403...
     * Planta 5 (Cota 12.9m - 14.4m): Nudos 501, 502, 503...

4. **Redimensionado del Grupo de Bombeo**:
   * Tras el cálculo de simultaneidad, comprobar la nueva curva de trabajo de la bomba. El caudal requerido del grupo pasará a ser de **3,18 l/s** (190,9 l/min) y la presión nominal requerida a la salida de la bomba probablemente deba aumentar de los $6,8\text{ bar}$ actuales para vencer las nuevas pérdidas por fricción incrementadas y mantener la presión dinámica en la boquilla más desfavorable (nudo 18) por encima de los 2 bar dinámicos reglamentarios.
