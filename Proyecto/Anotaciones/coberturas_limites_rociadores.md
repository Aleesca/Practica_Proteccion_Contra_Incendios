# ANÁLISIS DE COBERTURAS MÁXIMAS Y VALIDEZ DEL ROCIADOR SELECCIONADO (RA2845)

> **Ubicación**: [Proyecto/Anotaciones/coberturas_limites_rociadores.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/Anotaciones/coberturas_limites_rociadores.md)  
> **Asunto**: Análisis de las superficies y distancias de cobertura máximas según la norma UNE-EN 12845 y evaluación técnica de la validez del modelo prescrito (RA2845) a la luz del Anexo L.

---

## 1. Límites de Cobertura para Rociadores Estándar (UNE-EN 12845 Tabla 19)

La norma **UNE-EN 12845:2016+A1:2021** define de forma prescriptiva en su **Tabla 19** los límites máximos de cobertura y separación para rociadores estándar de techo o montantes (diferentes de los de pared):

### Tabla 1.1: Límites Prescriptivos de la Norma para Rociadores Estándar

| Clase de Riesgo | Superficie Máxima por Rociador ($A_{max}$) | Distancia Máxima entre Rociadores ($S$ y $D$) | Distancia Máxima a Paredes ($S/2$ o $D/2$) |
| :--- | :---: | :---: | :---: |
| **Riesgo Ligero (RL)** | **21,0 m²** | **4,6 m** | **2,3 m** |
| **Riesgo Ordinario (RO)** | **12,0 m²** | **4,0 m** | **2,0 m** |
| **Riesgo Extra (RE)** | **9,0 m²** | **3,7 m** | **1,85 m** |

*Nota: Para distribución al tresbolillo en Riesgo Ordinario (RO), la norma permite aumentar la distancia máxima a 4,6 m entre rociadores de la misma línea, pero manteniendo siempre la superficie máxima por rociador de 12,0 m².*

---

## 2. Rociadores de Cobertura Extendida (EC) y el Anexo L (Tecnología Especial)

Los rociadores de **Cobertura Extendida (EC)** (denominados en la traducción de la norma española como *"rociadores de cobertura ampliada"*) son componentes que quedan fuera de las tablas prescriptivas generales de la norma. 

### 2.1. Justificación Normativa según el Anexo L (Informativo)
El **Anexo L** de la norma UNE-EN 12845, titulado **"Tecnología Especial"**, da cobertura legal a estos sistemas al indicar lo siguiente:

> *"Esta norma europea cubre solo los tipos de rociador especificados en la Norma EN 12259-1. Durante los años anteriores a la preparación de esta norma se venían desarrollando nuevas tecnologías para aplicaciones especiales, incluyendo en particular [...] rociadores residenciales [y] rociadores de cobertura ampliada [...] La ingeniería de dichas aplicaciones está actualmente muy especializada. Está previsto que sean incluidas en futuras ediciones de esta norma."*

### 2.2. Viabilidad y Criterio de Diseño en España
Dado que el cuerpo prescriptivo principal de la norma UNE-EN 12845 no contiene tablas de dimensionamiento para rociadores de cobertura extendida, el marco técnico y de inspección en España (bajo el RIPCI) establece que:
1.  **Validez por Certificación**: El uso de estos rociadores es completamente válido y legal siempre que el producto cuente con una homologación emitida por un laboratorio de prestigio internacional acreditado (como **UL - Underwriters Laboratories** o **FM - Factory Mutual**).
2.  **Criterio de Diseño Predominante**: El diseño, la separación máxima y las demandas hidráulicas (presión y caudal) no se rigen por la Tabla 19 de la norma, sino por la **ficha técnica (datasheet) del fabricante**, la cual recoge los límites ensayados en laboratorio para obtener la marca de conformidad UL/FM.
3.  El fabricante debe certificar el caudal mínimo, la presión mínima residual y la separación máxima para garantizar que el patrón de descarga de agua cubra la superficie declarada manteniendo la densidad de diseño correspondiente.

---

## 3. Evaluación de Validez del Rociador Seleccionado (RA2845)

> [!CAUTION]
> **DIAGNÓSTICO: EL ROCIADOR SELECCIONADO ERA TOTALMENTE INVÁLIDO EN LOS CÁLCULOS V1 Y V2**
> Existe una sospecha técnica completamente fundada: el modelo **RA2845** no era válido en los esquemas de cálculo anteriores. A continuación se detallan los motivos normativos de esta invalidez y cómo se puede subsanar.

### 3.1. Incompatibilidad de Riesgo (La Razón Principal de Invalidez)
*   **En los cálculos V1 y V2**: El edificio se modeló bajo la clasificación de **Riesgo Ordinario 1 (RO1)**.
*   **Ficha técnica del rociador**: El modelo **RA2845** (de *AG Fire Sprinkler*) está catalogado y homologado por laboratorios externos (UL/FM) de forma exclusiva como:
    > **"Extended Coverage Light Hazard Pendent Sprinkler"** (Rociador colgante de cobertura extendida para **Riesgo Ligero - RL**).
*   **Infracción Normativa**: Las normas UNE-EN 12845 e instalaciones homologadas **prohíben terminantemente** instalar rociadores clasificados para Riesgo Ligero en sectores clasificados como Riesgo Ordinario (RO). Un rociador de Riesgo Ligero no está ensayado para controlar los incendios de mayor carga térmica de las actividades ordinarias. Por tanto, el diseño bajo RO1 con el rociador RA2845 era **ilegal y nulo**.

### 3.2. Violación de Cobertura en Riesgo Ordinario
*   En los cálculos V1 y V2, se asumió una cobertura por rociador de **24,01 m²** ($4,9\text{ m} \times 4,9\text{ m}$).
*   Si el sistema se considera **Riesgo Ordinario (RO1)**:
    *   La superficie máxima admisible para un rociador estándar es de **12,0 m²**.
    *   Para usar cobertura extendida en RO1 se requeriría un modelo homologado para Riesgo Ordinario (**ECOH** - *Extended Coverage Ordinary Hazard*), el cual tiene diámetros de boquilla mayores (K=115 o K=160) y exige presiones y caudales mucho más altos para garantizar la densidad de 5,0 mm/min.
    *   El modelo **RA2845** tiene un factor K=80 y **no está homologado** para dar cobertura extendida en RO.

---

## 4. Solución: Validación tras el Cambio a Riesgo Ligero (RL)

El rociador **RA2845** seleccionado se vuelve **100% VÁLIDO y LEGAL** únicamente si se aplica la propuesta de reclasificación del edificio a **Riesgo Ligero (RL)** detallada en [justificacion_riesgo_ligero.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/Anotaciones/justificacion_riesgo_ligero.md):

*   **Bajo Riesgo Ligero (RL)**: El uso del rociador RA2845 (ECLH, K=80) es correcto y está respaldado por su homologación de fabricante.
*   **Aplicación del Anexo L**: El diseño se acoge al Anexo L ("Tecnología especial") y se dimensiona según la ficha de producto certificada por UL para Riesgo Ligero:
    *   Para la cobertura de **4,9 m x 4,9 m (24,01 m²)**, el fabricante exige una presión mínima residual de **1,50 bar** (aportando un caudal de **98,4 l/min** por cabeza).
    *   Esta presión de 1,50 bar debe introducirse como **límite mínimo de cálculo** en el programa DMELECT/CYPE para los rociadores de la vivienda.
    *   El caudal de 98,4 l/min sobre la superficie de 24,01 m² equivale a una densidad de **4,10 mm/min**, superando holgadamente los **2,25 mm/min** exigidos por la UNE-EN 12845 para Riesgo Ligero.

## Archivos relacionados

*   [justificacion_riesgo_ligero.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/Anotaciones/justificacion_riesgo_ligero.md): Justificación formal de la reclasificación a RL para la memoria.
*   [justificacion_riesgo_ligero_limites.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/Anotaciones/justificacion_riesgo_ligero_limites.md): Límites hidráulicos del sistema combinados en RL.
*   [presion-minima-rociador-dmelect.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/Anotaciones/presion-minima-rociador-dmelect.md): Parámetros teóricos de presión mínima y factor K.
*   [catalogos-bies-rociadores.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/Anotaciones/catalogos-bies-rociadores.md): Selección del catálogo comercial Komtes/AG.
