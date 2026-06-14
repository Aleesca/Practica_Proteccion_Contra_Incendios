# Especificacion de redaccion: Introduccion e objetivos

## Objetivo del apartado

Introducir el contexto tecnico de la proteccion contra incendios en edificios residenciales y explicar que la practica busca familiarizar al alumno con el diseno, calculo y verificacion normativa de instalaciones de BIEs y rociadores automaticos.

## Subapartados propuestos

- Contexto de la proteccion contra incendios.
- Alcance de la practica.
- Objetivo general.
- Objetivos especificos.
- Criterios normativos de referencia.

## Contenido que debe cubrir

- Explicar que las instalaciones de PCI tienen como finalidad limitar el desarrollo del incendio, facilitar la intervencion y proteger a los ocupantes.
- Presentar las BIEs como medio manual de primera intervencion y los rociadores como sistema automatico de control o extincion inicial.
- Indicar que el edificio estudiado se modela con red comun de alimentacion, grupo de presion, BIEs y rociadores.
- Mantener los tres objetivos ya presentes en `main.tex`: diseno y calculo de BIEs, diseno y calculo de rociadores, analisis y comprobacion normativa.
- Anadir como objetivo transversal la interpretacion critica de los resultados hidraulicos.

## Normativa y criterios a citar

- CTE DB-SI, especialmente como marco general de seguridad en caso de incendio.
- RIPCI, Real Decreto 513/2017, para condiciones de equipos e instalaciones.
- UNE-EN 671-1 para BIEs de manguera semirrigida.
- UNE-EN 12845 para rociadores automaticos.
- Fichas tecnicas de fabricantes para la comprobacion de equipos seleccionados.

## Propuesta de redaccion

La proteccion contra incendios en los edificios combina medidas de prevencion, deteccion, evacuacion y extincion. Dentro de las instalaciones activas, las Bocas de Incendio Equipadas permiten una primera intervencion manual sobre el foco del incendio, mientras que los rociadores automaticos actuan de forma autonoma cuando se alcanza la temperatura de disparo del elemento termosensible.

El objetivo principal de esta practica es familiarizarse con los conceptos relativos a las instalaciones de proteccion contra incendios mediante el diseno y calculo de una instalacion interior compuesta por BIEs y rociadores automaticos. Para ello se parte de la geometria del edificio, se define el trazado de la red, se seleccionan equipos compatibles con la normativa aplicable y se comprueba el comportamiento hidraulico del sistema.

Los objetivos especificos son: disenar y calcular la red interior de BIEs; disenar y calcular la red interior de rociadores automaticos; analizar los resultados obtenidos en el programa de calculo; y comprobar que los valores de presion, caudal, velocidad y reserva de agua son coherentes con los criterios normativos y tecnicos adoptados.

## Datos o referencias internas utiles

- Figuras de apoyo: `IPCI.png`, `BIE_en_funcionamiento.png`, `Rocioador_en_funcionamiento.png`.
- Notas tecnicas: `Proyecto/Anotaciones/catalogos-bies-rociadores.md`.
- Normativa local del repositorio: `Normativa/DBSI.pdf`, `Normativa/Normas BIEs/`, `Normativa/Normas Rociadores/`.

## Pendientes antes de pasar a LaTeX

- Decidir si se menciona expresamente que la instalacion puede ser una mejora voluntaria en un edificio residencial o si esa discusion se reserva para resultados.
- Corregir en `main.tex` la errata "realtivos" cuando se migre la redaccion final.
