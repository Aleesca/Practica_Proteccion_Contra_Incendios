# Protocolo: Criterio de Selección de Rociadores Activos en DMelect

## 1. Justificación de la Zona de Simulación
Para la verificación hidráulica en DMelect, se debe seleccionar la zona **más desfavorable** de la instalación. Esta se sitúa en la **última planta** por dos motivos:
- **Cota geométrica:** Es el punto más alto del edificio, exigiendo la mayor presión estática.
- **Pérdida de carga:** Suele ser el punto más alejado del grupo de presión en términos de recorrido de tubería.

## 2. Definición del Área de Operación
Según la norma **UNE-EN 12845** para la clasificación **RO1 (Riesgo Ordinario 1)**:
- **Área de operación (sistema mojado):** 72 m².
- **Densidad de diseño:** 5,0 mm/min (5,0 L/min·m²).

Este área de 72 m² representa la superficie máxima sobre la que se supone que los rociadores funcionarán simultáneamente en un incendio de diseño. **No se debe activar la planta completa** (270 m²) ni la vivienda completa (~128 m²), ya que esto no es un escenario normativo y conduciría a un sobredimensionamiento irreal de bombas y tuberías.

## 3. Cálculo del Número de Rociadores a Activar
El número de rociadores a activar en DMelect se obtiene dividiendo el área de operación entre la superficie protegida por cada rociador:

### Caso A: Rociador estándar (Cobertura 12 m²)
- `72 m² / 12 m² = 6 rociadores`.
- Es el valor por defecto en DMelect para RO1.

### Caso B: Rociador de cobertura extendida RA2845 (Cobertura ~24 m²)
- `72 m² / 24,01 m² = 2,99 ≈ 3 rociadores`.
- Debido a la mayor eficiencia de cobertura, el incendio de diseño se contiene con menos puntos de descarga, pero manteniendo el caudal total proporcional al área de 72 m².

## 4. Procedimiento Operativo en DMelect
1. Identificar el ramal hidráulicamente más remoto en la última planta.
2. Seleccionar los **3 rociadores** (si se usa RA2845) o **6 rociadores** (si se usa estándar) situados al final de dicho ramal y ramales adyacentes hasta cubrir el área de **72 m²**.
3. En las propiedades de estos nudos, marcarlos como "en funcionamiento simultáneo".
4. Verificar que la presión residual en el rociador más desfavorable cumple con el mínimo requerido (1,5 bar para RA2845 o el valor derivado del cálculo por densidad).

## 5. Conclusión para la Memoria
La activación de **3/6 rociadores** en la zona remota de la última planta es el criterio técnicamente correcto porque:
- Representa el **escenario normativo de incendio localizado** (72 m²).
- Garantiza que el grupo de presión puede suministrar el caudal y presión necesarios en el punto más crítico.
- Evita el error de cálculo derivado de suponer un incendio generalizado en toda la planta, lo cual es incoherente con los principios de diseño de rociadores automáticos.

---
*Este protocolo se basa en las anotaciones de proyecto `superficie-rociadores.md` y `presion-minima-rociador-dmelect.md`, validadas mediante investigación normativa UNE-EN 12845.*
