# Especificacion de redaccion: Introduccion e objetivos

## Objetivo del apartado

Introducir el contexto tecnico de la proteccion contra incendios en edificios residenciales y explicar que la practica busca familiarizar al alumno con el diseno, calculo y verificacion normativa de instalaciones de BIEs y rociadores automaticos.

## Subapartados propuestos

El apartado puede organizarse como una secuencia de contexto, alcance, objetivo general, objetivos especificos y criterios normativos de referencia. La redaccion debe mantener continuidad entre esos bloques para que no parezcan epigrafes aislados.

## Contenido que debe cubrir

La introduccion debe explicar que las instalaciones de PCI tienen como finalidad limitar el desarrollo del incendio, facilitar la intervencion y proteger a los ocupantes. Conviene presentar las BIEs como medio manual de primera intervencion y los rociadores como sistema automatico de control o extincion inicial.

El texto debe indicar que el edificio estudiado se modela con una red comun de alimentacion, grupo de presion, BIEs y rociadores. Se mantendran los tres objetivos ya presentes en `main.tex`: diseno y calculo de BIEs, diseno y calculo de rociadores, y analisis y comprobacion normativa. Como objetivo transversal, se anadira la interpretacion critica de los resultados hidraulicos.

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

- Notas tecnicas: [catalogos de BIEs y rociadores](../Anotaciones/catalogos-bies-rociadores.md).
- Normativa local del repositorio: `../../Normativa/DBSI.pdf`, `../../Normativa/Normas BIEs/`, `../../Normativa/Normas Rociadores/`.

## Figuras a integrar

Las figuras tecnicas se incorporaran durante la redaccion de la memoria solo si ayudan a introducir visualmente los sistemas descritos. Todas llevaran como pie de figura la indicacion `Fuente: Elaboracion grupal`.

- `../../Practica_PCI_LaTeX/Figuras/IPCI.png`: contexto general de las instalaciones de proteccion contra incendios.
- `../../Practica_PCI_LaTeX/Figuras/BIE_en_funcionamiento.png`: apoyo visual para explicar las Bocas de Incendio Equipadas.
- `../../Practica_PCI_LaTeX/Figuras/Rocioador_en_funcionamiento.png`: apoyo visual para explicar los rociadores automaticos.

Las imagenes `../../Practica_PCI_LaTeX/Figuras/chimenea_recta.jpg`, `../../Practica_PCI_LaTeX/Figuras/ule.jpg` y `../../Practica_PCI_LaTeX/Figuras/escudo-ingenierias.png` quedan documentadas como material de portada o institucional, no como figuras tecnicas del cuerpo de la memoria.

## Pendientes antes de pasar a LaTeX

- Decidir si se menciona expresamente que la instalacion puede ser una mejora voluntaria en un edificio residencial o si esa discusion se reserva para resultados.
- Corregir en `main.tex` la errata "realtivos" cuando se migre la redaccion final.
