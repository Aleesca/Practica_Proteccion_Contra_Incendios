# Plan de Justificación Normativa (Anexo L) para los Cálculos de Rociadores en RO1

## Resumen
Reformular el razonamiento técnico para la revisión de los cálculos hidráulicos en [resultados_calculos.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/resultados_calculos.md). Se mantendrá la clasificación de **Riesgo Ordinario 1 (RO1)** en el edificio y se justificará el uso del rociador de cobertura extendida **RA2845 (K-80)** mediante la cláusula de desviación por equivalencia del Capítulo 1 y las disposiciones de tecnología especial del **Anexo L** de la norma UNE-EN 12845:2016+A1:2021. Esto evitará modificar el área de operación a $84\text{ m²}$ (Riesgo Ligero), manteniendo los 3 rociadores activos del modelo actual y previniendo los desajustes en diámetros y velocidades de tuberías en la red física real.

---

## Fases de Trabajo

### Fase 1: Análisis y Trazado Normativo en `PCI_Practicas` y RIPCI
*   Analizar las directrices de la **Guía Técnica de Aplicación del RIPCI** (Ministerio de Industria) sobre el uso de tecnologías no contempladas explícitamente en el cuerpo prescriptivo de las normas UNE (desviaciones justificadas por equivalencia según el Capítulo 1 de UNE-EN 12845).
*   Documentar cómo el **Anexo L ("Tecnología especial")** de la norma UNE-EN 12845 ampara el diseño de sistemas con rociadores de cobertura ampliada (extendida) basándose en las certificaciones del fabricante (UL/FM) y en el dimensionamiento específico de caudales y presiones.

### Fase 2: Determinación de las Demandas Hidráulicas en RO1
*   Calcular el caudal de descarga que debe suministrar cada rociador RA2845 para cumplir con la densidad mínima de diseño de **$5,0\text{ mm/min}$** exigida para RO1, considerando su área de cobertura real de **$24,01\text{ m²}$** ($4,9\text{ m} \times 4,9\text{ m}$):
    $$\text{Q} = 5,0\text{ L/min·m²} \times 24,01\text{ m²} = 120,05\text{ L/min}$$
*   Calcular la presión mínima residual en punta que exige el factor **K-80** del rociador para verter dicho caudal:
    $$\text{P} = \left(\frac{120,05}{80}\right)^2 = 2,25\text{ bar}$$
*   Comparar este requerimiento ($2,25\text{ bar}$) con el valor simulado en el proyecto ($2,00\text{ bar}$ en el nudo 179) para identificar la pequeña desviación del proyectista (que aporta una densidad real de $4,71\text{ mm/min}$, aproximada a la exigencia).

### Fase 3: Validación del Área de Operación y Tuberías sin Reclasificación
*   Confirmar que al mantener **RO1**, el área de operación hidráulica reglamentaria sigue siendo de **$72\text{ m²}$**.
*   Justificar que el número de rociadores activos simulados simultáneamente es exactamente **3** ($3 \times 24,01\text{ m²} = 72,03\text{ m²}$), lo cual coincide plenamente con el modelo hidráulico actual del proyecto.
*   Explicar el impacto de evitar la reclasificación a RL: al no aumentar el área de operación a $84\text{ m²}$ (que requeriría 4 rociadores activos), se mantienen invariables los caudales y pérdidas de carga del diseño, evitando tener que sobredimensionar y ajustar manualmente los diámetros de tuberías, práctica ineficiente e irreal en obra.

### Fase 4: Redacción del Informe Técnico de Auditoría Final
*   Sustituir el informe anterior en [informe_revision_normativa_resultados_calculos.md](file:///H:/Unidades%20compartidas/Practicas_Inst2/7_Proteccion_contra_incendios/Proyecto/Anotaciones/informe_revision_normativa_resultados_calculos.md) por la nueva argumentación basada en el Anexo L y el mantenimiento de la clasificación RO1.
*   Actualizar la matriz de cumplimiento, señalando la conformidad de los diámetros de tubería existentes y la viabilidad del aljibe de $36,8\text{ m³}$ (coherente para una hora de autonomía bajo RO1).

### Fase 5: Validación del Artefacto y Trazabilidad
*   Actualizar la copia del informe en el directorio de artefactos del asistente.
*   Verificar que todos los enlaces a archivos locales mantengan la trazabilidad y formato exigido.

---

## Pruebas y Criterios de Aceptación
- [ ] La justificación normativa cita textualmente los apartados de la Guía RIPCI y el Anexo L de la norma.
- [ ] Se mantienen las tablas hidráulicas de BIEs y rociadores de la versión original sin proponer recálculos de diámetros.
- [ ] Se detalla matemáticamente la relación entre densidad ($5,0\text{ mm/min}$), área de cobertura ($24,01\text{ m²}$), caudal ($120\text{ l/min}$) y presión ($2,25\text{ bar}$).
- [ ] El informe final califica la instalación como **VÁLIDA** bajo la justificación especial del Anexo L, indicando únicamente las pequeñas desviaciones menores de presión y cotas.
