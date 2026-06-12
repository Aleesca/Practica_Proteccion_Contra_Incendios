# JUSTIFICACIÓN TÉCNICA DE LA SIMULTANEIDAD Y LA BIE MÁS DESFAVORABLE

> **Ubicación**: [Proyecto/Anotaciones/justificacion_simultaneidad_BIEs.md](justificacion_simultaneidad_BIEs.md)  
> **Tema**: Justificación hidráulica y normativa de la apertura de dos Bocas de Incendio Equipadas (BIE 25) en un edificio con una BIE por planta.

---

## 1. Contexto de la Decisión del Proyectista

En el planteamiento inicial del diseño, se determinó que la **BIE de la última planta (Nudo 18, cota $14,4\text{ m}$)** es la más desfavorable de la instalación. Esta premisa es **geométricamente correcta**:
* Es el punto de consumo situado a mayor cota (altura física del edificio).
* Requiere el recorrido de tuberías más largo desde la sala de bombeo (cota $0\text{ m}$).
* Por lo tanto, es el punto que experimenta la mayor pérdida de presión estática (gravedad) y dinámica (fricción en la montante vertical).

Sin embargo, el dimensionamiento hidráulico completo de la instalación no debe limitarse al funcionamiento aislado de esta BIE única.

---

## 2. Requisito Legal de Simultaneidad (RIPCI)

La normativa española de protección contra incendios, establecida en el **Reglamento de Instalaciones de Protección contra Incendios (RIPCI, RD 513/2017)** y en la Guía Técnica de Aplicación, impone el siguiente criterio de diseño para las redes de BIEs:

> **RIPCI Anexo I (Sección 4.ª Sistemas de Bocas de Incendio Equipadas)**:  
> *"La red de BIE deberá garantizar durante una hora, como mínimo, el caudal descargado por **las dos** hidráulicamente más desfavorables..."*

Esto significa que, independientemente de la distribución de las BIEs en el edificio, el cálculo debe justificar que el sistema responde correctamente cuando **dos BIEs funcionan a la vez**.

---

## 3. Identificación de las BIEs en Columna Montante

Dado que la instalación consta de **una BIE por planta**, las dos BIEs que se encuentran en la situación hidráulicamente más desfavorable son las situadas a mayor altura:

1. **Primera BIE más desfavorable**: BIE de la última planta (**Nudo 18**, Planta 5, cota $14,4\text{ m}$).
2. **Segunda BIE más desfavorable**: BIE de la penúltima planta (**Nudo 15**, Planta 4, cota $11,8\text{ m}$).

Para que el modelo hidráulico sea normativamente válido, ambas BIEs deben configurarse como **activas (abiertas)** en el software de cálculo simultáneamente.

---

## 4. Impacto Hidráulico en la Red

La diferencia entre calcular para 1 BIE (diseño previo) o para 2 BIEs simultáneas (diseño normativo) altera drásticamente los resultados hidráulicos:

### 4.1. Duplicación del Caudal en la Montante Común
* **Con 1 BIE abierta (Nudo 18)**: El caudal que sube por la montante vertical es de **$1,59\text{ l/s}$** ($95,47\text{ l/min}$).
* **Con 2 BIEs abiertas (Nudos 18 y 15)**: El caudal que asciende desde la sala de bombas hasta la planta 4 (donde se conecta la BIE del nudo 15) pasa a ser de **$3,18\text{ l/s}$** ($190,9\text{ l/min}$).

### 4.2. Multiplicación de las Pérdidas de Carga
Según la fórmula de Hazen-Williams para pérdidas por rozamiento en tuberías:
$$h_f = r_{ij} \times Q^{1,852}$$
Al duplicar el caudal ($Q$) en los tramos de la montante común (Líneas 6, 15, 18, 17), las pérdidas de carga en estos tubos aumentan por un factor de:
$$2^{1,852} \approx 3,61 \text{ veces}$$
Las pérdidas en esos tramos pasarán de aproximadamente $1,32\text{ mca}$ a unos $4,76\text{ mca}$.

### 4.3. Consecuencia en las Presiones en Boquilla
Este incremento en las pérdidas de carga comunes reducirá la presión dinámica disponible en la entrada de las BIEs. Si el grupo de bombeo está dimensionado al límite para 1 BIE (aportando $69,34\text{ mca}$ de altura), al abrir la segunda BIE la presión en la punta de lanza de la última planta (Nudo 18) **caerá por debajo de los $2\text{ bar}$ dinámicos obligatorios**, invalidando la instalación ante una inspección.

---

## 5. Justificación del Volumen del Depósito (Reserva de Agua)

El volumen del aljibe del sistema contra incendios está directamente ligado a la simultaneidad de BIEs exigida por el RIPCI (mínimo de 60 minutos de autonomía):

* **Volumen con 1 BIE (No conforme)**:
  $$V = 1 \text{ BIE} \times 95,47 \text{ l/min} \times 60 \text{ min} = 5.728 \text{ litros}$$
* **Volumen normativo con 2 BIEs (Conforme)**:
  $$V = 2 \text{ BIEs} \times 100 \text{ l/min} \times 60 \text{ min} = 12.000 \text{ litros} \quad (12\text{ m}^3)$$

El diseño actual presenta un **déficit de $6.272\text{ litros}$** (un 52% menos del volumen legal requerido), lo cual constituye una infracción crítica de seguridad y de normativa.

---

## 6. Pasos para la Corrección en el Software de Cálculo

Para subsanar esta deficiencia en el modelo de cálculo:
1. **Modificar demandas**: Configurar la BIE del Nudo 15 (cota 11.8m) para que esté activa (demanda abierta) al mismo tiempo que la BIE del Nudo 18 (cota 14.4m).
2. **Dimensionar el grupo de presión**: Ajustar el caudal de diseño de la bomba a un mínimo de **$3,18\text{ l/s}$** ($190,9\text{ l/min}$) y verificar que la altura manométrica ($H$) de la bomba garantiza la presión mínima de $2\text{ bar}$ en punta de lanza en el Nudo 18 y el Nudo 15.
3. **Modificar la reserva en la memoria**: Indicar un volumen mínimo de acumulación de agua de **12.000 litros**.

## Archivos relacionados

- [resultados_calculos_BIE.md](resultados_calculos_BIE.md): Cálculo base con una sola BIE activa.
- [informe_revision_calculos_bie.md](informe_revision_calculos_bie.md): Informe que marca la simultaneidad como incidencia crítica.
- [sobre_altura_cotas.md](sobre_altura_cotas.md): Contexto de cotas para identificar las BIEs desfavorables.
- [catalogos-bies-rociadores.md](catalogos-bies-rociadores.md): Características de la BIE seleccionada.
