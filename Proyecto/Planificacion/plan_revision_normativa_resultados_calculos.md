# Plan: Revision Normativa de `resultados_calculos.md`

> Source PRD: solicitud de revision de `Proyecto/resultados_calculos.md`

## Resumen

Revisar los calculos de la instalacion PCI documentados en `Proyecto/resultados_calculos.md` para detectar posibles irregularidades y comprobar su coherencia con la normativa aplicable. El trabajo debe incluir contraste documental con el notebook `PCI_practicas`, consulta de referencias tecnicas web mediante Exa MCP y comparacion con proyectos reales de ingenieria de caracteristicas similares.

El resultado esperado es un informe tecnico en Markdown con veredicto por comprobacion, lista de incidencias o dudas, y una conclusion sobre si la instalacion calculada parece razonable para un edificio de 5 plantas sobre rasante, un sotano de aparcamiento, 2 viviendas por planta, 270.882 m2 utiles por planta y 14.5 m de altura total.

## Cambios clave

- Revisar los datos de entrada y supuestos declarados en `Proyecto/resultados_calculos.md`.
- Contrastar los calculos con normativa y criterios tecnicos aplicables a:
  - viviendas;
  - zonas comunes;
  - sotano de aparcamiento;
  - BIEs;
  - rociadores, si aparecen en el proyecto;
  - red hidraulica, reserva de agua y grupo de presion, si forman parte del diseno.
- Identificar posibles irregularidades como:
  - uso incorrecto de superficies o alturas;
  - simultaneidad mal aplicada;
  - presiones insuficientes;
  - caudales incoherentes;
  - perdidas de carga no justificadas;
  - criterios normativos incompletos o mal interpretados.
- Consultar como referencia:
  - `Normativa/DBSI.pdf`;
  - normas UNE de BIEs y rociadores disponibles en el repositorio;
  - `PCI_practicas` como apoyo doctrinal;
  - consultas tecnicas y proyectos reales localizados con Exa MCP.
- Emitir una comparativa razonada con 3-5 casos reales o memorias tecnicas similares para valorar si la dimension del edificio y la solucion PCI son habituales o atipicas.

## Fases de revision

### Fase 1: Inventario de datos y supuestos

Extraer de `Proyecto/resultados_calculos.md` todos los parametros relevantes para la revision: geometria, uso, alturas, superficies, equipos PCI, caudales, presiones, tramos criticos, simultaneidad, reservas y cualquier hipotesis de calculo.

### Criterios de aceptacion

- [ ] Quedan identificados los datos geometricos y funcionales del edificio.
- [ ] Se separan resultados finales de valores intermedios.
- [ ] Se detectan posibles faltas de informacion que impidan una verificacion normativa completa.
- [ ] Los datos ambiguos quedan marcados para revision posterior.

### Fase 2: Matriz normativa aplicable

Construir una matriz de comprobacion con los requisitos normativos que afecten al caso, separando viviendas, zonas comunes y sotano de aparcamiento.

### Criterios de aceptacion

- [ ] Cada requisito tiene fuente normativa o tecnica asociada.
- [ ] La matriz indica si el proyecto cumple, no cumple o requiere interpretacion.
- [ ] Se incorporan criterios sobre BIEs, rociadores y red hidraulica cuando proceda.
- [ ] La relacion entre requisito, dato del proyecto y resultado queda trazada.

### Fase 3: Revision de calculos hidraulicos y de instalacion

Comprobar la coherencia tecnica de los calculos: presiones, caudales, perdidas de carga, diametros, simultaneidad, cobertura y condiciones de servicio.

### Criterios de aceptacion

- [ ] Se revisa la coherencia de unidades y magnitudes.
- [ ] Se identifican valores fuera de rango o poco justificables.
- [ ] Se detectan incoherencias entre la red calculada y el criterio normativo.
- [ ] Las observaciones distinguen entre error de calculo, falta de justificacion e incumplimiento.

### Fase 4: Contraste con fuentes externas y proyectos reales

Usar el notebook `PCI_practicas` y consultas con Exa MCP para localizar referencias tecnicas, ejemplos de proyecto y criterios de comprobacion usados en la practica profesional.

### Criterios de aceptacion

- [ ] Se consultan fuentes tecnicas suficientes para contrastar el caso.
- [ ] La comparacion con proyectos reales se usa como referencia de razonabilidad, no como norma.
- [ ] La conclusion incluye si el edificio y su solucion PCI se ajustan a rangos habituales o muestran valores atipicos.
- [ ] Se conservan enlaces o referencias consultables para las afirmaciones relevantes.

### Fase 5: Informe final de revision

Redactar el informe tecnico final con resumen ejecutivo, tabla de comprobaciones, irregularidades detectadas, comparativa con casos reales y conclusion tecnica.

### Criterios de aceptacion

- [ ] El informe responde de forma clara si la instalacion parece normal para el edificio descrito.
- [ ] Cada posible irregularidad incluye descripcion, criterio afectado e impacto.
- [ ] Las conclusiones diferencian hechos, interpretaciones y dudas por falta de datos.
- [ ] El documento final queda listo para usarse como memoria o anexo de revision.

## Pruebas y validacion

- Verificar que todos los apartados relevantes de `Proyecto/resultados_calculos.md` quedan cubiertos.
- Comprobar que cada conclusion tecnica tiene referencia normativa, documental o comparativa.
- Revisar que la conclusion final no confunde adecuacion normativa con normalidad estadistica de proyectos reales.
- Confirmar que el informe conserva trazabilidad entre datos, criterio evaluado y resultado.
- Hacer una lectura final del Markdown para comprobar orden, claridad y consistencia terminologica.

## Supuestos

- El trabajo es documental y de revision; no modifica el modelo ni recalcula la instalacion.
- La revision final debe quedar en formato Markdown dentro de `Proyecto/Anotaciones/` o en una ubicacion equivalente de revision documental si asi se decide despues.
- La comparacion con proyectos reales se limitara a 3-5 referencias relevantes con criterio tecnico razonado.
- La altura total de 14.5 m se usara como dato de contraste, sin asumir que equivale automaticamente a altura de evacuacion.
- Si faltan datos en `resultados_calculos.md`, el informe los señalara como limitacion y no forzara una conclusion definitiva.
