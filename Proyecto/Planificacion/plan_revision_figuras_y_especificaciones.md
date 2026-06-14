# Plan: Revision de Figuras y Enlaces en Especificaciones

## Resumen

Actualizar los archivos de `Proyecto/Especificaciones/` para que indiquen que figuras en formato `.jpg` y `.png` de `Practica_PCI_LaTeX/Figuras/` se deben integrar durante la redaccion de la memoria, siempre con la fuente `Fuente: Elaboracion grupal`. En paralelo, normalizar el estilo de todos los archivos de especificaciones para que predomine la prosa, los bullet points sean escasos y ninguno comience en negrita. Tambien se enlazaran las especificaciones con los archivos de apoyo de `Proyecto/Anotaciones/`.

## Decisiones de Implementacion

- Revisar las imagenes tecnicas o explicativas de `Practica_PCI_LaTeX/Figuras/`: `BIE_en_funcionamiento.png`, `Rocioador_en_funcionamiento.png`, `IPCI.png`, `Inicio_Tramo_y_BIE.png`, `definicion_plantas.png`, `Perfil_Plantas.png`, `chimenea_recta.jpg`, `ule.jpg` y `escudo-ingenierias.png`.
- Integrar como figuras del cuerpo tecnico solo las imagenes que aportan contenido de redaccion; los logotipos y la imagen de portada quedaran documentados como material de portada.
- Anadir en cada especificacion afectada una seccion breve de figuras a integrar, con nombre de archivo, uso previsto y la fuente prevista.
- Incorporar una directriz comun de estilo para todos los archivos de especificaciones: predominio de prosa, pocos bullets y sin bullets que arranquen en negrita.
- Convertir las referencias a anotaciones en enlaces Markdown relativos hacia `Proyecto/Anotaciones/`.

## Fases

### Fase 1: Inventario y asignacion de figuras

Revisar todas las imagenes `.jpg` y `.png` y asignarlas a los apartados de memoria donde aportan contexto, metodologia o resultados. La portada y los elementos institucionales quedaran separados del cuerpo tecnico.

**Criterio de aceptacion:** cada figura tecnica queda asociada a un apartado concreto o marcada como reutilizable con motivo claro.

### Fase 2: Actualizacion de especificaciones con figuras

Incorporar en las especificaciones las figuras recomendadas para la redaccion, indicando siempre `Fuente: Elaboracion grupal` y el papel que desempenan en el texto.

**Criterio de aceptacion:** cada figura incluida tiene archivo, finalidad y fuente prevista.

### Fase 3: Normalizacion del estilo de redaccion

Revisar los cinco archivos de especificaciones para que las instrucciones favorezcan prosa escrita, reduzcan listas innecesarias y eviten bullets cuyo inicio este en negrita.

**Criterio de aceptacion:** las directrices quedan aplicadas de forma homogenea y compatibles con la restriccion especifica del resumen.

### Fase 4: Enlace con anotaciones

Sustituir o complementar las referencias planas a anotaciones por enlaces relativos a los archivos reales de `Proyecto/Anotaciones/`.

**Criterio de aceptacion:** cada especificacion enlaza las anotaciones que justifican sus datos, criterios o decisiones tecnicas.

### Fase 5: Verificacion final

Comprobar que todos los archivos de `Proyecto/Especificaciones/` mantienen coherencia interna, que los enlaces apuntan a archivos existentes y que las figuras mencionadas existen en `Practica_PCI_LaTeX/Figuras/`.

**Criterio de aceptacion:** no hay figuras inexistentes, enlaces rotos ni directrices de estilo contradictorias.

## Asignacion Inicial Recomendada

- `01_introduccion_objetivos.md`: `IPCI.png`, `BIE_en_funcionamiento.png`, `Rocioador_en_funcionamiento.png`.
- `02_metodologia.md`: `definicion_plantas.png`, `Perfil_Plantas.png`, `Inicio_Tramo_y_BIE.png`.
- `03_resultados_discusion.md`: `Inicio_Tramo_y_BIE.png` solo si se usa para explicar puntos singulares; si no, el apartado puede quedar apoyado en tablas y anexos.
- `00_resumen.md`: sin figuras en el resumen, por su restriccion de prosa breve y directa.
- `04_conclusiones.md`: sin figuras nuevas, salvo remision general a planos y anexos.
- Material no tecnico o de portada: `chimenea_recta.jpg`, `ule.jpg`, `escudo-ingenierias.png`.

## Plan de Verificacion

- Comprobar que la lista de imagenes mencionadas coincide con los archivos existentes en `Practica_PCI_LaTeX/Figuras/`.
- Revisar que los enlaces a `Proyecto/Anotaciones/` son relativos, correctos y trazables.
- Verificar que los bullets restantes son escasos y no empiezan en negrita.
- Confirmar que cada figura tecnica integra la indicacion de `Fuente: Elaboracion grupal`.
- Mantener `00_resumen.md` dentro de su limite de extension y con prosa exclusiva.

## Supuestos

- No se modificaran aun los archivos LaTeX.
- Las imagenes de logotipos y portada no se integraran como figuras tecnicas del cuerpo de la memoria.
- La fuente comun para las figuras revisadas sera exactamente `Fuente: Elaboracion grupal`.
