# Especificacion de redaccion: Resumen

## Objetivo del apartado

Redactar una sintesis inicial de la memoria que permita entender, antes de entrar en el desarrollo, que se ha disenado una instalacion de proteccion contra incendios para un edificio residencial, que sistemas se han incluido, que metodologia se ha seguido y cual es el resultado global de la verificacion hidraulica.

## Contenido que debe cubrir

- Presentar el alcance de la practica: diseno y calculo de una red interior de BIEs y una red de rociadores automaticos.
- Indicar que el calculo se ha desarrollado mediante un modelo hidraulico de la instalacion, con comprobacion de caudales, presiones, velocidades y reserva de agua.
- Explicar que la memoria justifica tanto la seleccion del trazado como la eleccion de equipos comerciales.
- Anticipar el cumplimiento global de los requisitos de funcionamiento, destacando los puntos mas desfavorables.
- Mencionar que los calculos completos, planos y fichas tecnicas se incorporan como anexos, sin citar referencias concretas dentro del resumen.

## Directrices de estilo y extension

- Extension maxima: 250 palabras.
- Redaccion exclusivamente en prosa, sin listas, tablas, ecuaciones, pies de pagina ni referencias bibliograficas.
- No usar abreviaciones. Escribir siempre los terminos completos, por ejemplo, "Bocas de Incendio Equipadas" en lugar de "BIEs".
- Estilo tipo resumen ejecutivo directo: debe contar lo esencial de la practica de forma breve, como una explicacion formal a un superior durante un trayecto corto en ascensor.
- Mantener formalidad tecnica, pero priorizar claridad, resultado y alcance frente a desarrollo teorico.
- Ir al grano: que se ha disenado, como se ha comprobado, que resultados principales se obtienen y cual es la conclusion tecnica.

## Datos y resultados a incorporar

- Grupo de presion: 10,53 L/s y 99,63 mca.
- BIEs simultaneas: nudos 122 y 125.
- Caudal total BIEs: 200,91 L/min.
- Rociadores activos: nudos 140, 141 y 142.
- Caudal total rociadores: 430,87 L/min.
- Reserva total estimada: 37.906,87 L.
- Punto critico BIE: nudo 125, con 2,000 bar en boquilla.
- Punto critico rociador: nudo 142, con 2,829 bar.

## Fuentes de apoyo

- `Proyecto/resultados_calculos.md`.
- `Proyecto/Anotaciones/informe_revision_normativa_resultados_calculos.md`.
- Anexo de calculos incluido en `Practica_PCI_LaTeX/Figuras/Anejo_calculo.pdf`.
- Planos incluidos en `Practica_PCI_LaTeX/Figuras/Planos/`.

## Propuesta de redaccion

La memoria desarrolla el diseno y la comprobacion hidraulica de una instalacion de proteccion contra incendios para un edificio residencial, formada por una red de Bocas de Incendio Equipadas y una red de rociadores automaticos. El trabajo parte de la definicion del trazado, la seleccion de equipos comerciales y la construccion de un modelo de calculo que permite verificar presiones, caudales, velocidades y reserva de agua.

El resultado principal es una instalacion capaz de alimentar simultaneamente los puntos de consumo mas desfavorables considerados. El grupo de presion calculado proporciona 10,53 litros por segundo a 99,63 metros de columna de agua. La demanda total de las Bocas de Incendio Equipadas es de 200,91 litros por minuto y la de los rociadores automaticos es de 430,87 litros por minuto. La reserva de agua necesaria se estima en 37.906,87 litros.

La comprobacion confirma que la Boca de Incendio Equipada mas desfavorable alcanza la presion minima exigida en boquilla y que el rociador mas desfavorable dispone de margen suficiente de funcionamiento. En conjunto, el diseno queda tecnicamente justificado, con los calculos, planos y fichas tecnicas incorporados como documentacion complementaria.

## Pendientes antes de pasar a LaTeX

- Confirmar si el resumen debe incluir referencias normativas explicitas o reservarlas para metodologia y resultados.
- Revisar que los valores finales de `Proyecto/resultados_calculos.md` no hayan cambiado antes de incorporar el texto a `main.tex`.
- Comprobar que la version final no supera 250 palabras y no contiene abreviaciones, referencias, pies de pagina ni ecuaciones.
