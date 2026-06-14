# Especificacion de redaccion: Metodologia

## Objetivo del apartado

Describir como se ha construido el modelo de calculo: datos introducidos, definicion de la topologia del edificio, seleccion del esquema de instalacion, justificacion del trazado y eleccion de equipos y materiales.

## Subapartados propuestos

- Datos introducidos en el programa.
- Topologia del edificio y seleccion del esquema de instalacion.
- Justificacion del trazado elegido.
- Equipos instalados y materiales de la instalacion.

## Datos introducidos en el programa

Debe explicarse que el modelo hidraulico se ha definido a partir de las plantas y cotas del edificio, incluyendo sotano y plantas sobre rasante. La descripcion debe recoger la introduccion de nudos, ramas, montantes y derivaciones hasta BIEs y rociadores, junto con las longitudes reales o equivalentes de tuberia.

Tambien se indicaran el material de tuberia, el coeficiente de Hazen-Williams, los diametros nominales e interiores, las perdidas secundarias consideradas y los elementos terminales empleados. El apartado debe cerrar esta parte explicando el grupo de presion y las condiciones de demanda simultanea.

Valores de referencia ya documentados:

- Metodo de calculo: Hazen-Williams.
- Perdidas secundarias: 20 %.
- Velocidad maxima de referencia: 10 m/s.
- BIE: presion minima de boquilla 2 bar y maxima de boquilla 5 bar.
- Rociadores: valores minimos segun clase de riesgo y criterio adoptado.

## Topologia del edificio y esquema de instalacion

El texto debe explicar que la instalacion se organiza mediante una red comun alimentada por grupo de presion, desde la que se distribuye el caudal hacia las BIEs y hacia los ramales de rociadores. Conviene describir:

La existencia de una montante principal, las derivaciones por plantas hacia zonas comunes y viviendas, la integracion de BIEs en zonas accesibles y la distribucion de rociadores sobre la superficie protegida. Tambien debe explicarse la relacion entre planos de planta, perfil vertical y esquema unifilar.

## Figuras a integrar

Las figuras metodologicas deben incorporarse para explicar la geometria y el criterio de modelado, siempre con el pie `Fuente: Elaboracion grupal`.

- `../../Practica_PCI_LaTeX/Figuras/definicion_plantas.png`: definicion de plantas y cotas del edificio.
- `../../Practica_PCI_LaTeX/Figuras/Perfil_Plantas.png`: relacion entre perfil vertical, cotas y plantas.
- `../../Practica_PCI_LaTeX/Figuras/Inicio_Tramo_y_BIE.png`: esquema inicial de trazado, tramo y ubicacion de BIE.

Los planos del anexo `../../Practica_PCI_LaTeX/Figuras/Planos/` se citaran como documentacion complementaria, no como sustitucion de estas figuras de apoyo.

## Justificacion del trazado elegido

La redaccion debe justificar que el trazado busca reducir recorridos innecesarios, mantener una lectura clara de la red y llevar la alimentacion por zonas comunes y montantes verticales. Tambien debe explicar que la ubicacion elegida garantiza accesibilidad y cobertura de las BIEs, mientras que los rociadores cubren la superficie protegida respetando separaciones y condicionantes geometricos.

El texto debe anadir que el trazado mantiene las velocidades dentro del limite de calculo y evita cambios de diametro innecesarios una vez comprobada la viabilidad hidraulica.

Debe mencionarse que la superficie protegida de planta considerada para rociadores es 270,882 m2, formada por dos viviendas de 127,965 m2 y una zona comun de 14,952 m2. Esta superficie sirve para definir el alcance fisico de proteccion, no para sustituir el area de operacion hidraulica normativa.

## Equipos instalados y materiales

Equipos seleccionados:

- BIE 25 mm IMP Workfire 300/B2, manguera semirrigida de 30 m, factor K = 42, toma adicional de 45 mm y montaje empotrado.
- Rociador Tyco Series EC-11, SIN TY5237, factor K = 161,3, cobertura extendida, presion minima residual de ficha 0,83 bar, redondeada en documentacion a 0,8 bar.
- Tuberia de acero con coeficiente Hazen-Williams C = 120, segun resultados del modelo.

El apartado debe explicar que la seleccion de equipos se apoya en fichas tecnicas reales incorporadas como anexo y en criterios de compatibilidad normativa.

## Propuesta de redaccion

La metodologia seguida parte de la definicion geometrica del edificio y de la introduccion de la red en el programa de calculo. Para cada tramo se introducen los nudos de origen y destino, la longitud, el material, el diametro nominal y las condiciones de perdida de carga. El calculo se realiza mediante Hazen-Williams, considerando perdidas secundarias del 20 % y una velocidad maxima de referencia de 10 m/s.

La instalacion se organiza mediante una red comun alimentada por un grupo de presion. Desde esta red parten las montantes y derivaciones que abastecen las BIEs y los rociadores automaticos. La disposicion adoptada permite relacionar el plano de planta con el perfil vertical y con el esquema unifilar, de forma que los puntos de consumo quedan identificados por nudo y cota.

El trazado se ha elegido buscando continuidad hidraulica, facilidad de ejecucion y cobertura efectiva de las zonas protegidas. Las BIEs se situan en puntos accesibles de las zonas comunes, mientras que los rociadores se distribuyen sobre la superficie protegida de la planta, formada por viviendas y zona comun. La seleccion de equipos se completa con una BIE 25 mm empotrada y un rociador de cobertura extendida, ambos respaldados por documentacion tecnica de fabricante.

## Fuentes de apoyo

- [Resultados de calculo](../resultados_calculos.md).
- [Superficie de rociadores](../Anotaciones/superficie-rociadores.md).
- [Catalogos de BIEs y rociadores](../Anotaciones/catalogos-bies-rociadores.md).
- [Altura y cotas](../Anotaciones/sobre_altura_cotas.md).

## Pendientes antes de pasar a LaTeX

- Confirmar si se incluye una tabla resumida de datos de entrada o si se remite todo al anexo de calculo.
- Revisar que los nombres de figuras usados en LaTeX coincidan exactamente con los archivos existentes.
