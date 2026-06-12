 **poner las cotas a 0 puede ser correcto** si estás usando la planta base como referencia del edificio y luego dejas que el programa calcule el resto por alturas de planta. En dmELECT la planta de referencia es la que fija la cota absoluta, y los nudos de conexión entre plantas se enlazan por el colector vertical asignado. [dmelect](https://dmelect.com/wp-content/uploads/2024/04/ManualEdificios-compress.pdf)

## Lo importante aquí
Si la conexión vertical parte del **BIE** y del **rociador**, lo esencial no es tanto que la cota del colector sea 0 por sí misma, sino que:
- El nudo esté asociado al **colector vertical correcto**.
- La **planta de referencia** y la **cota absoluta** hagan que el perfil quede coherente.
- El colector vertical del BIE/rociador se coloque en la **planta donde realmente nace ese tramo**. [dmelect](https://dmelect.com/wp-content/uploads/2024/04/Manual-Instal-Elect-URBANIZACION-compress.pdf)

## Qué significa para tu caso
Si has puesto todas las cotas a 0, eso puede servir como base de cálculo, pero solo si la planta donde empieza el sistema coincide con la planta de referencia o con la lógica de alturas que quieres dibujar. [dmelect](https://dmelect.com/wp-content/uploads/2024/04/ManualEdificios-compress.pdf)
Como dmELECT conecta plantas mediante colectores verticales y ubica sus nudos según la cota de la planta activa, el problema suele venir de una **referencia mal elegida**, no del valor 0 en sí. [dmelect](https://dmelect.com/centro-de-ayuda/preguntas-frecuentes-generales/)

## Sobre BIE y rociador
En instalaciones de protección contra incendios, los elementos como **BIEs y rociadores** se consideran equipos del sistema y pueden estar vinculados a la red vertical del edificio. [dit.ietcc.csic](https://dit.ietcc.csic.es/wp-content/uploads/2020/02/Comunicado-web-PPR-BIEs-y-Rociadores.pdf)
Por tanto, si el colector vertical nace en el sótano, lo lógico es que esa montante se defina desde el nivel donde realmente arranca la red, y que la cota de ese nudo refleje esa posición. [dmelect](https://dmelect.com/wp-content/uploads/2024/04/Manual-Instal-Elect-URBANIZACION-compress.pdf)

## Recomendación práctica
- Si quieres que el sistema “empiece” en el sótano, deja el **sótano como nivel inferior real**.
- Usa la **planta de referencia** solo para que las cotas del edificio queden bien escaladas.
- En el perfil, comprueba que el primer nudo del colector del BIE/rociador esté asignado al colector vertical correcto y no esté heredando otra planta. [dmelect](https://dmelect.com/centro-de-ayuda/preguntas-frecuentes-generales/)

En resumen: **cota 0 puede estar bien**, pero solo si coincide con tu referencia de edificio; para el BIE y el rociador lo decisivo es que la **montante vertical** esté bien asociada desde el sótano y no desde una planta superior. [dit.ietcc.csic](https://dit.ietcc.csic.es/wp-content/uploads/2020/02/Comunicado-web-PPR-BIEs-y-Rociadores.pdf)

## Archivos relacionados

- [resultados_calculos_BIE.md](resultados_calculos_BIE.md): Cotas y presiones calculadas en la red BIE.
- [informe_revision_calculos_bie.md](informe_revision_calculos_bie.md): Incidencias de nudos, cotas y trazabilidad.
- [justificacion_simultaneidad_BIEs.md](justificacion_simultaneidad_BIEs.md): Uso de las cotas para localizar BIEs desfavorables.
- [presion-minima-rociador-dmelect.md](presion-minima-rociador-dmelect.md): Presión mínima de rociadores en relación con los nudos.
