# Justificación Técnica y Económica: Selección de Rociador Único (AG GA1311)

**Referencia:** Análisis derivado de las optimizaciones requeridas en `ANOTACIONES_PRACTICA.pdf`.
**Asunto:** Justificación del uso de un rociador de Cobertura Extendida (EC) de 36 m² en espacios reducidos (10-20 m²) y su impacto económico global en la instalación de PCI del edificio residencial.

---

## 1. El falso mito del "Sobredimensionamiento"

Al observar que el modelo **AG GA1311** tiene una capacidad de cobertura de hasta 36 m², es intuitivo pensar que colocarlo en una habitación de 10 m² o 20 m² supone un sobredimensionamiento ineficiente. Sin embargo, en el diseño de redes de rociadores, el comportamiento es diferente:

*   **Hidráulicamente:** El rociador no "gasta" más agua por estar en un cuarto pequeño. Descarga el caudal que le dicta la presión de la red en ese nudo.
*   **Físicamente:** En una habitación de 10 m², el patrón de agua alcanzará las paredes casi de inmediato. Esto produce un efecto conocido como *wall wetting* (mojado de paredes), el cual es altamente deseable en protección contra incendios porque enfría los paramentos y evita que el fuego se propague a las habitaciones colindantes.

## 2. Análisis Económico: ¿Por qué es la opción más barata?

La decisión de unificar todo el edificio con el modelo **AG GA1311 (Cobertura Extendida y Respuesta Rápida)** se basa en una optimización global de costes, donde el ahorro en la instalación supera con creces cualquier sobrecoste del equipo.

### A. Reducción drástica de Mano de Obra y Tubería (El mayor coste)
El mayor gasto en una instalación de PCI no son las cabezas de los rociadores, sino **la mano de obra, los metros de tubería de acero y los accesorios (codos, tes, manguitos)**. 
*   Al usar un rociador de Cobertura Extendida en los salones y pasillos comunes, **se reduce hasta en un 50% el número de rociadores** en esas zonas. 
*   Menos rociadores significa menos ramales que soldar o ranurar, menos soportes al techo y muchísimo menos tiempo de instalación por planta.

### B. Economía de Escala (Unificación de Compras)
*   Comprar 500 unidades de un solo modelo (GA1311) permite negociar mejores descuentos con el proveedor (AG Fire Sprinkler) que comprar 300 de un modelo estándar y 200 de uno extendido.
*   **Repuestos y Mantenimiento:** El edificio solo necesitará almacenar un tipo de rociador de repuesto y una sola llave de montaje. Las tapas embellecedoras serán idénticas en todas las estancias, mejorando la estética y abaratando su coste.

### C. Prevención de Errores de Ejecución
Tener un modelo mixto (pequeños para habitaciones, extendidos para pasillos) genera un riesgo alto en obra: si el instalador intercambia los rociadores por error, el pasillo quedará desprotegido (un rociador estándar no llegará a cubrirlo) y la inspección obligará a desmontar el techo y repetir la instalación. Unificar el modelo elimina este riesgo a coste cero.

## 3. La "Penalización" Hidráulica a considerar

Para ser rigurosos en el cálculo, el uso de este rociador único tiene una única contrapartida que debe asumirse en el diseño de DMelect/CYPE:
*   Los rociadores de Cobertura Extendida exigen una **presión mínima de trabajo mayor** (aprox. 1.5 a 2.0 bar) que los estándar (aprox. 0.5 bar) para poder lanzar el agua tan lejos.
*   Al poner este rociador en el baño más alejado de la última planta (el nudo más desfavorable), el software nos obligará a garantizar esa presión alta allí, lo que requerirá un **grupo de bombeo (Bomba PCI) ligeramente más potente**.

**Conclusión Económica:** El leve incremento en el precio de la bomba principal se amortiza sobradamente con el enorme ahorro en metros de tubería, piezas especiales y cientos de horas de mano de obra al reducir los puntos de descarga en todas las plantas del edificio. Por tanto, el modelo **AG GA1311** es la opción más económica, segura y versátil.

## Archivos relacionados

- [catalogos-bies-rociadores.md](catalogos-bies-rociadores.md): Selección técnica de BIEs y rociadores.
- [presion-minima-rociador-dmelect.md](presion-minima-rociador-dmelect.md): Penalización hidráulica del rociador de cobertura extendida.
- [superficie-rociadores.md](superficie-rociadores.md): Superficies protegidas y límites de cobertura.
- [areas.md](areas.md): Superficies por estancia usadas en la estimación.
