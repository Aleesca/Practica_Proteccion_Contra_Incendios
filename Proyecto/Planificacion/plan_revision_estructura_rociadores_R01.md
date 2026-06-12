# Plan: Revision de Estructura de Rociadores R01

## Resumen

Revisar `Proyecto/Anotaciones/catalogos-bies-rociadores.md` para reorganizar y completar la parte de rociadores, separando claramente tecnologias, aplicaciones y condiciones de trabajo. La clase de riesgo ya esta seleccionada y es **R01**, por lo que la busqueda y validacion de rociadores debe alinearse con esa clasificacion.

La revision debe apoyarse en busquedas con Exa MCP, priorizando fabricantes o distribuidores espanoles, y contrastando la seleccion con la normativa descrita en `PCI_practicas`.

## Cambios clave

- Reestructurar la seccion de rociadores en bloques claros:
  - **Rociadores en contacto con agua**: sistemas humedos, tuberia llena de agua, respuesta directa ante activacion termica.
  - **Rociadores en contacto con aire a presion**: sistemas secos y sistemas supervisados con aire/nitrogeno, con agua retenida aguas arriba de la valvula.
  - **Tecnologias de activacion**: ampolla de vidrio, elemento fusible, respuesta estandar, respuesta rapida, ESFR, residencial y cobertura extendida.
  - **Configuraciones fisicas**: pendent, upright, sidewall, oculto, empotrado, seco y anticongelante si aplica.
  - **Parametros tecnicos comparables**: factor K, temperatura nominal, orientacion, acabado, presion de trabajo, certificaciones, norma aplicable y adecuacion a riesgo **R01**.
- Investigar con Exa MCP catalogos y fichas tecnicas de marcas preferentemente espanolas o con distribucion tecnica consolidada en Espana.
- Para cada familia de rociadores incluida, documentar:
  - Uso previsto.
  - Tipo de sistema compatible.
  - Tecnologia de activacion.
  - Condicion del fluido en reposo: agua o aire/nitrogeno presurizado.
  - Compatibilidad con la clase de riesgo **R01**.
  - Normas, certificaciones u homologaciones indicadas por el fabricante.
  - Enlace a ficha tecnica o catalogo fuente.

## Fases de revision

### Fase 1: Mapa tecnico de rociadores

Definir la estructura nueva de la seccion de rociadores antes de insertar productos concretos.

### Criterios de aceptacion

- [ ] Existe una taxonomia clara entre rociadores para sistemas humedos y sistemas secos/supervisados.
- [ ] Se distinguen tecnologias de activacion, orientacion y aplicacion.
- [ ] La estructura permite comparar productos de distintos fabricantes.
- [ ] La clase de riesgo **R01** aparece como criterio fijo de seleccion.

### Fase 2: Busqueda y seleccion de fuentes

Usar Exa MCP para localizar catalogos, fichas tecnicas y documentacion normativa de productos.

### Criterios de aceptacion

- [ ] Se priorizan resultados de fabricantes o distribuidores espanoles.
- [ ] Cada producto o familia citada tiene una fuente tecnica verificable.
- [ ] Se descartan paginas comerciales sin ficha tecnica suficiente.
- [ ] Se registra la trazabilidad de cada fuente mediante enlace.
- [ ] La seleccion se filtra por aplicabilidad al riesgo **R01**.

### Fase 3: Rociadores en contacto con agua

Completar la seccion de sistemas humedos.

### Criterios de aceptacion

- [ ] Se explican los sistemas donde la tuberia permanece llena de agua.
- [ ] Se incluyen rociadores habituales para este uso: pendent, upright, sidewall, ocultos o empotrados cuando proceda.
- [ ] Se indican tecnologias de respuesta estandar, rapida y cobertura extendida si aparecen en fuentes validas.
- [ ] Cada ejemplo incluye parametros tecnicos minimos: factor K, temperatura, orientacion, certificacion y adecuacion a **R01**.

### Fase 4: Rociadores en contacto con aire a presion

Completar la seccion de sistemas secos o supervisados.

### Criterios de aceptacion

- [ ] Se explica la diferencia tecnica entre tuberia humeda y tuberia con aire/nitrogeno presurizado.
- [ ] Se incluyen rociadores secos, sistemas secos, preaccion o supervisados cuando correspondan.
- [ ] Se aclara que el agua llega al rociador tras apertura de valvula o activacion del sistema.
- [ ] Se documentan limitaciones relevantes: riesgo de congelacion, tiempos de descarga, corrosion, mantenimiento y compatibilidad con **R01**.

### Fase 5: Contraste normativo y limpieza editorial

Alinear el contenido final con la normativa de referencia y mejorar la legibilidad del documento.

### Criterios de aceptacion

- [ ] Las afirmaciones normativas quedan ligadas a la referencia correspondiente de `PCI_practicas`.
- [ ] La clase de riesgo **R01** se mantiene como hipotesis de diseno ya seleccionada.
- [ ] No se presentan productos como validos si la ficha tecnica no muestra cumplimiento o certificacion suficiente.
- [ ] El documento separa claramente explicacion tecnica, comparacion de productos y referencias.
- [ ] La redaccion queda homogenea con el resto del catalogo.

## Pruebas y validacion

- Verificar que todos los enlaces de catalogo o ficha tecnica funcionan.
- Comprobar que cada rociador queda clasificado en una sola categoria principal: agua o aire/nitrogeno presurizado.
- Confirmar que cada producto incluido es coherente con la clase de riesgo **R01**.
- Revisar que no haya duplicidades entre tecnologias, orientaciones y aplicaciones.
- Validar que las normas citadas coinciden con la terminologia usada en `PCI_practicas`.
- Hacer una lectura final del Markdown para comprobar jerarquia de encabezados, tablas y referencias.

## Supuestos

- La clase de riesgo **R01** ya esta definida y no forma parte de esta revision.
- La revision se limita al contenido documental del catalogo, sin modificar calculos hidraulicos ni diseno de instalacion.
- La preferencia por marcas espanolas aplica salvo que no existan fuentes tecnicas suficientes para una tecnologia concreta.
- Cuando una marca internacional sea necesaria, se justificara por cobertura tecnica o disponibilidad normativa.
- El resultado esperado es una version revisada de `Proyecto/Anotaciones/catalogos-bies-rociadores.md` con trazabilidad completa de fuentes.
