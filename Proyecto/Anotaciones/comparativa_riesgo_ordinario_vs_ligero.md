# ESTUDIO COMPARATIVO DE ALTERNATIVAS DE DISEÑO: RO1 VS RIESGO LIGERO
## Red de Protección contra Incendios del Edificio Residencial

> **Archivos de Cálculo de Referencia**: 
> *   **Riesgo Ordinario 1 (RO1)**: [resultados_calculos.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/resultados_calculos.md)  
> *   **Riesgo Ligero (RL)**: [resultado_RLigero.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/resultado_RLigero.md)  
> **Normativa de Aplicación**: Código Técnico de la Edificación (CTE DB-SI) y Norma UNE-EN 12845.

---

## 1. Introducción

Este documento presenta una comparativa técnica y económica entre dos alternativas de diseño para la red de rociadores automáticos y BIEs del edificio residencial. Se evalúa el impacto de clasificar la zona de viviendas bajo la hipótesis de **Riesgo Ordinario 1 (RO1)** frente a la hipótesis de **Riesgo Ligero (RL)**, esta última simulada con **4 rociadores activos simultáneamente** tal como exige la norma UNE-EN 12845 para esta categoría de riesgo.

---

## 2. Tabla Comparativa de Parámetros Hidráulicos y de Diseño

La siguiente tabla resume los resultados de las dos simulaciones calculadas en el software:

| Parámetro Hidráulico / Diseño | Alternativa 1: Riesgo Ordinario 1 (RO1) | Alternativa 2: Riesgo Ligero (RL) | Diferencia Técnica (RL vs RO1) |
| :--- | :---: | :---: | :--- |
| **Nº de Rociadores Activos** | 3 rociadores | 4 rociadores | **+1 rociador activo** en RL. |
| **Presión Mínima Rociador ($P_{min}$)** | 0,57 bar | 0,70 bar | **+0,13 bar** (+22.8% de presión de boquilla en RL). |
| **Caudal Nominal Rociadores ($Q_{roc}$)** | **430,87 L/min** (7,18 L/s) | **584,55 L/min** (9,74 L/s) | **+153,68 L/min** (+35.6% de caudal en RL). |
| **Caudal Nominal BIEs ($Q_{bie}$)** | **200,91 L/min** (3,35 L/s) | **201,84 L/min** (3,36 L/s) | Prácticamente idéntico (~0%). |
| **Caudal Total de Diseño ($Q_{total}$)** | **10,53 L/s** (631,78 L/min) | **13,11 L/s** (786,39 L/min) | **+2,58 L/s** (+24.5% de caudal en RL). |
| **Presión del Grupo de Bombeo** | **99,63 mca** (9,77 bar) | **112,28 mca** (11,01 bar) | **+12,65 mca** (+12.7% de presión en RL). |
| **Autonomía Rociadores** | **60 minutos** | **30 minutos** | **-30 minutos** (Reducción a la mitad en RL). |
| **Reserva Rociadores** | **25.852,12 L** | **17.536,54 L** | **-8.315,58 L** (-32.1% en RL). |
| **Reserva BIEs (60 min)** | **12.054,75 L** | **12.110,24 L** | Equivalente. |
| **Reserva Total del Aljibe** | **37.906,87 L** | **29.646,78 L** | **-8.260,09 L** (-21.8% en RL). |
| **Presión Entrada BIE 122 (Planta 2ª)**| **6,300 bar** (Sobrepresión) | **6,411 bar** (Sobrepresión) | Aumenta la sobrepresión dinámica en RL. |
| **Velocidad Máxima en Tuberías** | **8,62 m/s** (Línea 123 - Dn32) | **9,51 m/s** (Línea 2 - Dn40) | Mayor velocidad general en la red en RL. |

---

## 3. Análisis de Impacto Técnico y Económico

### 3.1. Demanda del Grupo de Bombeo (Bomba y Presión)
*   **Paradoja del Riesgo Ligero**: Aunque intuitivamente el término "Riesgo Ligero" sugiere un sistema menos exigente, hidráulicamente ocurre lo contrario. Para RL, la norma UNE-EN 12845 exige una presión dinámica mínima superior en el rociador (**0,70 bar** frente a 0,57 bar en RO1) y un mayor número de rociadores activos simultáneamente (**4** en lugar de 3).
*   **Consecuencia**: El caudal de rociadores se incrementa en un **35.6%** ($584,55\text{ L/min}$) y la presión necesaria de la bomba sube a **112,28 mca** (11,01 bar). Esto exige un motor de bomba de mayor potencia y un consumo energético superior.

### 3.2. Reserva de Agua y Volumen del Aljibe
*   **Ventaja del Riesgo Ligero**: En RL, el tiempo de autonomía exigido por normativa se reduce a **30 minutos** (frente a los 60 minutos obligatorios en RO1).
*   **Consecuencia**: A pesar de que el caudal de rociadores en RL es mayor, el menor tiempo de autonomía compensa el volumen total. La reserva de rociadores baja a **17.536,54 L** (un ahorro de más de 8.300 litros). El depósito total necesario baja de **38 m³** a **29,6 m³**, lo que reduce considerablemente el coste de construcción del aljibe y el espacio ocupado en el edificio.

### 3.3. Velocidades e Dimensionado de la Red
*   En la alternativa de Riesgo Ligero, la velocidad en la salida de la bomba (Línea 2, Dn40) alcanza un valor muy crítico de **9,51 m/s** debido al caudal de 13,11 L/s.
*   En la montante vertical superior (Líneas 122 y 123), el aumento de caudal en RL a 11,33 L/s genera velocidades de **8,22 m/s** a pesar de que ambos tramos están dimensionados en **40 mm**.

---

## 4. Análisis Normativo (UNE-EN 12845)

*   **Clasificación de Viviendas**: Según el Anexo A de la norma UNE-EN 12845, los edificios de viviendas y residenciales de baja altura se clasifican de forma estándar como **Riesgo Ligero (RL)**.
*   **Conformidad**: Ambas opciones son reglamentariamente viables si se dimensionan correctamente, pero la hipótesis de **Riesgo Ligero (RL)** es la que mejor se ajusta a la realidad de un edificio residencial convencional de 5 plantas.

---

## 5. Recomendación y Veredicto de Diseño

Desde un enfoque práctico y de viabilidad del proyecto:

1.  **Si se prioriza el coste de obra y el espacio (Recomendado)**:
    *   **Alternativa a elegir: Riesgo Ligero (RL)**.
    *   **Motivo**: Permite instalar un aljibe más pequeño (ahorro de casi **8.300 litros** de agua y espacio útil en sótano).
    *   **Acciones necesarias en el software**:
        *   Mantener el diámetro de la montante superior en **40 mm** (Líneas 122 y 123) ya que con el mayor caudal de RL, reducirlo a 32 mm dispararía la presión y las pérdidas.
        *   Instalar una válvula reductora de presión en la toma de la BIE 122, ya que la presión de entrada dinámica alcanza los **6,411 bar** (límite RIPCI es 6,00 bar).

2.  **Si se prioriza una bomba más pequeña y menores velocidades**:
    *   **Alternativa a elegir: Riesgo Ordinario 1 (RO1)**.
    *   **Motivo**: El caudal de diseño de rociadores es menor ($430,87\text{ L/min}$), lo que permite que la bomba trabaje a menor presión (**99,63 mca**) y las velocidades de la red sean más moderadas.
