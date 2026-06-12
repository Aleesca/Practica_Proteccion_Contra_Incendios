# Informe de Auditoría Técnica: Revisión de Cálculos PCI V2

## 1. Introducción
Este informe presenta los resultados de la auditoría técnica realizada sobre el archivo `Proyecto/resultados_calculos_V2.md`, contrastándolos con el Plan de Revisión (`plan_revision_resultados_calculos_v2.md`), la normativa aplicable (RIPCI, CTE DB-SI, UNE-EN 12845) y la ficha técnica del rociador **Reliable RA2845**.

## 2. Inventario Trazable de Resultados (Fase 1)
| Parámetro | Valor en V2 | Unidad | Elemento/Nodo | Observación |
| --- | --- | --- | --- | --- |
| Caudal Bomba | 9.94 | l/s | Bomba 7 | 596.4 l/min |
| Presión Bomba | 96.04 | mca | Bomba 7 | ~9.41 bar |
| Caudal BIEs | 95.46 | l/min | Nodo 162 | **Solo 1 BIE activa** |
| Presión BIE | 2.00 | bar | Nodo 162 | Presión en boquilla consignada |
| Caudal Rociadores | 501.00 | l/min | Nudos 179-196 | 4 rociadores activos |
| Presión Rociador | 2.256 | bar | Nodo 195 | Nodo más desfavorable |
| Reserva BIE | 5,727.58 | l | Aljibe | Basada en 1 BIE |
| Reserva Rociador | 30,059.89 | l | Aljibe | - |

## 3. Hallazgos Críticos y No Conformidades (Fase 2 y 3)

### 3.1. Incumplimiento de Simultaneidad de BIEs (Crítico)
- **Criterio Normativo (RIPCI):** Se debe garantizar el funcionamiento de las **dos** BIEs hidráulicamente más desfavorables durante 60 minutos.
- **Estado Actual:** El cálculo contempla únicamente la activación de **una BIE** (Nodo 162).
- **Impacto:** El caudal de diseño y las pérdidas de carga en la montante están infravalorados. La apertura de una segunda BIE real provocaría una caída de presión por debajo de los 2 bar reglamentarios.

### 3.2. Insuficiencia de la Reserva de Agua (Crítico)
- **Criterio Normativo:** $2 \text{ BIEs} \times 100 \text{ l/min} \times 60 \text{ min} = 12,000$ litros (mínimo).
- **Estado Actual:** $5,727.58$ litros (para BIEs).
- **Impacto:** El aljibe no cumple con la autonomía legal de 60 minutos para el sistema de BIEs.

### 3.3. Exceso de Presión en Boquilla de BIE (Relevante)
- **Criterio Técnico/Normativo:** La presión dinámica en la boquilla no debe superar los 5 bar para evitar riesgos de retroceso al usuario.
- **Estado Actual:** La presión dinámica en el Nodo 162 es de **5.16 bar**.
- **Recomendación:** Instalar un reductor de presión o ajustar el punto de consigna de la bomba si es compatible con los rociadores.

## 4. Revisión del Sistema de Rociadores (Fase 4 y 5)

### 4.1. Configuración del Rociador RA2845
- **Modelo:** Reliable RA2845 (K=80).
- **Punto Comercial Mínimo:** 1.5 bar para cobertura de 4.9m x 4.9m (24.01 m²).
- **Hallazgo:** El software DMELECT tiene configurado un mínimo de **0.57 bar** (predeterminado para Riesgo Ordinario), lo cual es inconsistente con la ficha técnica del modelo seleccionado.
- **Cumplimiento Técnico:** Aunque la configuración es errónea, la presión real calculada en el nudo más desfavorable (**2.256 bar**) supera el mínimo de 1.5 bar del fabricante, por lo que el sistema es hidráulicamente viable para ese punto.

### 4.2. Área de Operación y Número de Rociadores
- **Criterio (UNE-EN 12845 - RO1):** Área de operación de 72 m².
- **Criterio Cobertura:** Si se usa cobertura estándar (12 m²/rociador), se requieren 6 rociadores. Si se justifica "Cobertura Extendida" (24 m²/rociador), se requieren 3.
- **Estado Actual:** 4 rociadores activos ($4 \times 24.01 = 96$ m²).
- **Conclusión:** El diseño es conservador respecto a la superficie de 72 m², siempre que se incluya en la memoria la justificación técnica de la "Cobertura Extendida" del modelo RA2845.

## 5. Conclusiones y Recomendaciones (Fase 6)

### Estado Global: **NO CONFORME**
Los cálculos de la V2 presentan deficiencias normativas críticas en el sistema de BIEs que invalidarían la certificación de la instalación.

### Acciones Recomendadas:
1. **Recalcular BIEs:** Activar simultáneamente el Nodo 162 y el siguiente más desfavorable (Planta 4).
2. **Aumentar Reserva:** Ajustar el volumen total del aljibe a un mínimo de 12,000 litros (BIE) + reserva de rociadores.
3. **Corregir Parámetros Sprinkler:** Cambiar la presión mínima en DMELECT de 0.57 bar a **1.5 bar** para reflejar la realidad del componente RA2845.
4. **Justificación Técnica:** Documentar formalmente el uso de rociadores de cobertura extendida para validar la retícula de diseño frente a la norma UNE-EN 12845.
