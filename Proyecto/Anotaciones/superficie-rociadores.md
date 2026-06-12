# Superficie y clase de riesgo para rociadores

Para la instalacion de rociadores automaticos se debe distinguir entre cuatro conceptos que no se calculan de la misma forma:

1. **Superficie real protegida:** superficie fisica donde se deben dibujar rociadores.
2. **Clase de riesgo:** clasificacion normativa segun el uso, la carga de fuego, la combustibilidad y la compartimentacion.
3. **Area de operacion:** superficie teorica de calculo hidraulico que da la UNE-EN 12845 segun la clase de riesgo.
4. **Cobertura maxima por rociador:** superficie geometrica maxima que puede proteger cada rociador individual.

La superficie total de la planta no determina por si sola la clase de riesgo. Sirve para saber que zonas deben protegerse, estimar el numero de rociadores y justificar otros apartados de la memoria, pero la clase de riesgo se determina al aplicar la UNE-EN 12845 sobre el uso real del edificio y sus condiciones.

## Superficie real protegida

Para el plano de rociadores se debe considerar la planta completa protegida, incluyendo viviendas y zonas comunes, salvo excepciones concretas admitidas por la norma tras comprobar carga de fuego y compartimentacion.

Datos medidos de la planta:

| Zona | Superficie util |
| --- | ---: |
| Vivienda 1 | 127,965 m2 |
| Vivienda 2 | 127,965 m2 |
| Zona comun | 14,952 m2 |
| **Total** | **270,882 m2** |

La zona comun donde se ubica la BIE se incluye dentro de la superficie protegida. Solo podrian omitirse zonas como aseos incombustibles sin almacenamiento combustible, escaleras cerradas o conductos verticales cerrados sin material combustible, siempre que esten construidos como compartimentos resistentes al fuego y la omision quede justificada.

## Determinacion de la clase de riesgo

La clase de riesgo no queda fijada en esta anotacion. Se debe determinar en el momento de aplicar el diseno, siguiendo este orden:

1. Comprobar el uso principal: residencial vivienda.
2. Verificar si existen locales de riesgo especial: trasteros, aparcamiento, almacenes, cuartos tecnicos con carga combustible, cocinas industriales u otros usos con carga de fuego superior.
3. Comprobar la compartimentacion resistente al fuego de viviendas y zonas comunes.
4. Aplicar la clase de riesgo que corresponda segun UNE-EN 12845 y, si procede, el CTE DB-SI para los locales especiales.

Segun UNE-EN 12845, el **Riesgo Ligero (RL)** exige actividades con baja carga de fuego y combustibilidad, y que no exista ningun compartimento mayor de **126 m2** con resistencia al fuego minima de 30 minutos.

Por tanto, queda pendiente esta comprobacion:

- Si cada vivienda se considera un unico compartimento resistente al fuego, cada una mide **127,965 m2**, por lo que supera el limite de 126 m2.
- Si existen compartimentos internos justificables, con resistencia al fuego suficiente y condiciones normativas adecuadas, se verificara si puede mantenerse una clase inferior.
- Si aparecen locales de riesgo especial, se clasificaran por separado y podrian exigir criterios mas desfavorables.

## Parametros a consultar segun la clase finalmente elegida

Una vez determinada la clase de riesgo, se consultan los parametros de diseno. Para las clases previsibles en este caso:

| Clase | Densidad de diseno | Area de operacion, sistema mojado | Cobertura maxima por rociador | Separacion maxima normal |
| --- | ---: | ---: | ---: | ---: |
| RL | 2,25 mm/min | 84 m2 | 21,0 m2/rociador | 4,6 m |
| RO1 | 5,0 mm/min | 72 m2 | 12,0 m2/rociador | 4,0 m |

Ademas, para la separacion entre rociadores debe respetarse la distancia minima normativa de 2,0 m, salvo medidas especificas para evitar que rociadores adyacentes se mojen entre si.

## Uso de la superficie de 270,882 m2

La superficie medida de **270,882 m2** no debe emplearse como area de operacion hidraulica. El area de operacion la fija la norma segun la clase de riesgo finalmente adoptada.

Esta superficie si sirve para:

- Definir el alcance fisico de la proteccion: viviendas y zona comun.
- Estimar el numero aproximado de rociadores antes de dibujar la reticula.
- Comprobar que toda la planta queda cubierta respetando separaciones maximas y distancias a paredes.
- Justificar ocupacion y sectorizacion en la memoria, cuando corresponda segun CTE DB-SI.
- Verificar que la superficie protegida por un puesto de control queda por debajo de los limites normativos aplicables.

El numero final de rociadores se calculara solo cuando se haya fijado la clase de riesgo y se haya dibujado la distribucion real sobre el plano, porque las habitaciones, pasillos, paredes, obstaculos y distancias maximas pueden aumentar el numero respecto a una division directa de superficie entre cobertura maxima.

## Archivos relacionados

- [areas.md](areas.md): Superficies por estancia que complementan la superficie total.
- [presion-minima-rociador-dmelect.md](presion-minima-rociador-dmelect.md): Presión y número de rociadores derivados de la superficie.
- [catalogos-bies-rociadores.md](catalogos-bies-rociadores.md): Selección de rociadores según riesgo y cobertura.
- [justificacion_economica_rociador_unico.md](justificacion_economica_rociador_unico.md): Justificación de modelo único sobre las superficies protegidas.
- [sobre_altura_cotas.md](sobre_altura_cotas.md): Relación entre distribución de rociadores y referencia vertical.
