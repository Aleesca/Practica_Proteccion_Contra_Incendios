# Especificacion de redaccion: Resultados y discusion

## Objetivo del apartado

Interpretar los resultados hidraulicos del modelo y demostrar que la instalacion funciona en los escenarios considerados. El apartado debe ir mas alla de listar resultados: debe explicar que significan, donde estan los puntos criticos y por que el diseno se considera valido.

## Subapartados propuestos

- Analisis de la verificacion hidraulica mediante mapa de estados.
- Analisis de los puntos singulares mas desfavorables.
- Verificacion normativa y criterios de aceptacion.
- Discusion tecnica del diseno adoptado.

## Analisis de la verificacion hidraulica mediante mapa de estados

Debe explicarse que el mapa de estados permite localizar visualmente:

- Tramos con caudal significativo.
- Tramos sin demanda en el escenario calculado.
- Velocidades elevadas.
- Nudos con menor presion dinamica.
- Elementos terminales activos en la hipotesis de calculo.

Resultados clave:

- Grupo de presion: 10,53 L/s, 99,63 mca.
- Caudal total de diseno: 631,78 L/min.
- Velocidad maxima: 8,62 m/s en la linea 123, por debajo del limite de 10 m/s.
- Se acepta la geometria actual sin cambio general de diametros.

## Puntos singulares mas desfavorables

El texto debe separar BIEs y rociadores.

Para BIEs:

- Se consideran dos BIEs activas simultaneamente.
- BIE nudo 122: planta 2, cota 11,8 m, 105,451 L/min, 6,300 bar de entrada y 2,441 bar en boquilla.
- BIE nudo 125: planta 3, cota 14,4 m, 95,462 L/min, 5,163 bar de entrada y 2,000 bar en boquilla.
- La BIE 125 es el punto mas desfavorable por alcanzar exactamente la presion minima de boquilla.
- La BIE 122 presenta sobrepresion de entrada respecto al limite de 6,0 bar y se resolvera con valvula reductora de presion en el armario.

Para rociadores:

- Se consideran tres rociadores activos simultaneamente.
- Nudos activos: 140, 141 y 142, a cota 15,4 m.
- Caudales: 152,764 L/min, 143,515 L/min y 134,591 L/min.
- El rociador 142 es el mas desfavorable, con 2,829 bar.
- El caudal total de rociadores es 430,87 L/min.

## Verificacion normativa y reserva de agua

La redaccion debe incluir una tabla o parrafo con estos criterios:

- Simultaneidad BIEs: dos mas desfavorables, cumple.
- Presion minima BIE: mayor o igual que 2,0 bar en boquilla, cumple en el nudo 125.
- Caudal BIE 25 mm: valores calculados superiores al minimo de producto documentado.
- Presion rociadores: valor minimo calculado superior al criterio adoptado.
- Reserva BIEs: 12.054,75 L para 60 min.
- Reserva rociadores: 25.852,12 L para 60 min.
- Reserva combinada: 37.906,87 L.

## Discusion tecnica

La discusion debe tratar cuatro ideas:

- El modelo queda hidraulicamente equilibrado porque los puntos criticos cumplen las presiones minimas.
- La velocidad maxima es elevada pero admisible dentro del limite de calculo.
- La valvula reductora en la BIE 122 es una medida puntual y mas razonable que redimensionar toda la red.
- La reserva de agua resultante es elevada para un edificio residencial, pero coherente con la hipotesis de diseno adoptada.

Tambien puede mencionarse, si se desea un enfoque critico, la comparacion entre RO1 y Riesgo Ligero:

- RO1 reduce el caudal de rociadores y la presion de bombeo frente a la alternativa RL.
- RL reduce el volumen de reserva por menor autonomia, pero exige mas caudal y mayor presion de bomba.
- En la memoria final debe evitarse presentar esta comparacion como una contradiccion: debe aparecer como decision de diseno o como reflexion tecnica.

## Propuesta de redaccion

Los resultados obtenidos muestran que la red satisface las condiciones hidraulicas del escenario de calculo. El grupo de presion proporciona un caudal de 10,53 L/s a 99,63 mca, suficiente para alimentar simultaneamente las BIEs y los rociadores considerados. La velocidad maxima registrada es de 8,62 m/s en la linea 123, valor elevado pero inferior al limite de 10 m/s empleado como criterio de comprobacion.

En la red de BIEs, los puntos mas desfavorables se localizan en los nudos 122 y 125. La BIE del nudo 125 alcanza una presion de boquilla de 2,000 bar, por lo que constituye el caso limite de la instalacion. La BIE del nudo 122 presenta una presion de entrada de 6,300 bar; esta situacion se resolvera mediante la instalacion de una valvula reductora de presion en el propio armario, manteniendo el trazado y los diametros del modelo.

En la red de rociadores, el escenario de calculo activa los nudos 140, 141 y 142. El rociador mas desfavorable es el del nudo 142, con una presion de 2,829 bar y un caudal de 134,591 L/min. Estos valores garantizan margen suficiente respecto al criterio de funcionamiento adoptado para los rociadores seleccionados.

La reserva total de agua asciende a 37.906,87 L, resultado de sumar la reserva asociada a BIEs y la reserva asociada a rociadores. Aunque este volumen supone una exigencia significativa para un edificio residencial, es coherente con las hipotesis de calculo y con el tiempo de autonomia considerado.

## Fuentes de apoyo

- `Proyecto/resultados_calculos.md`.
- `Proyecto/Anotaciones/informe_revision_normativa_resultados_calculos.md`.
- `Proyecto/Anotaciones/comparativa_riesgo_ordinario_vs_ligero.md`.
- `Proyecto/Anotaciones/presion-minima-rociador-dmelect.md`.
- `Proyecto/Anotaciones/justificacion_simultaneidad_BIEs.md`.

## Pendientes antes de pasar a LaTeX

- Confirmar si se incluira una tabla de verificacion normativa completa en el cuerpo o solo una version resumida.
- Revisar la coherencia entre los valores finales del anexo PDF y `Proyecto/resultados_calculos.md`.
- Decidir si la comparacion RO1/RL entra en el cuerpo principal o queda solo como criterio interno de discusion.
