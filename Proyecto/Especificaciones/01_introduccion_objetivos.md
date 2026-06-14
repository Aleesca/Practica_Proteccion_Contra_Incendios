# Especificacion de redaccion: Introduccion e objetivos

## Objetivo del apartado

Introducir el contexto tecnico de la proteccion contra incendios en edificios residenciales y explicar que la practica busca familiarizar al alumno con el diseno, calculo y verificacion normativa de instalaciones de BIEs y rociadores automaticos.

## Subapartados propuestos

El apartado se organiza en base al contexto, alcance de los sistemas, marco normativo, objetivos principales y especificos.

## Contenido definitivo (Cerrado)

### Contexto y Marco Normativo

En el diseño arquitectónico y de ingeniería contemporáneo, la seguridad frente a incendios representa uno de los requerimientos más estrictos e ineludibles. En los edificios destinados a uso residencial colectivo, donde la densidad de ocupación y los tiempos de evacuación en caso de emergencia pueden elevar sustancialmente el riesgo para las vidas humanas, la implementación de medidas eficaces de protección activa contra incendios resulta indispensable. La protección activa comprende todos aquellos equipos y sistemas instalados con el objeto de detectar la presencia de fuego, controlar su propagación radial o vertical, y proceder a su mitigación o extinción definitiva. La funcionalidad de estos sistemas se divide fundamentalmente entre la intervención temprana manual y la supresión autónoma e inmediata.

Las Bocas de Incendio Equipadas (BIE) representan el exponente clásico de los sistemas de protección activa de accionamiento manual y primera intervención. Compuestas estructuralmente por una manguera, un soporte giratorio, una válvula de paso y una boquilla lanza con posibilidad de regular el chorro de agua, permiten a los ocupantes del propio edificio o a los equipos de primera intervención desplegar una línea de agua presurizada para combatir el fuego en su fase de gestación o desarrollo inicial. Su flexibilidad radica en el control directo del chorro de agua hacia el foco del incendio, lo que maximiza la eficiencia en la aplicación del agente extintor y permite enfriar las superficies adyacentes de manera dirigida. No obstante, al depender de la acción humana para su puesta en marcha y manejo, su efectividad está sujeta a la presencia física de personas capacitadas y a las condiciones de visibilidad y temperatura ambiental en el sector afectado.

Por el contrario, los sistemas de rociadores automáticos (sprinklers) constituyen sistemas autónomos y automáticos de supresión de incendios que no requieren de la intervención humana directa. Estos emisores están distribuidos estratégicamente a nivel de techo y permanecen cerrados por medio de un elemento térmicamente sensible —como un bulbo de vidrio que contiene un líquido expansible al calor o un fusible de aleación eutéctica—. Cuando la columna de gases calientes de un incendio incide sobre el rociador y este alcanza una temperatura predeterminada de activación, el elemento fusible se rompe o funde, liberando el obturador y permitiendo la descarga inmediata de un patrón de agua pulverizada en forma de parábola sobre el foco ígneo. Esta respuesta autónoma no solo controla localmente el incendio y limita el incremento de temperatura ambiental en el recinto, sino que además mitiga la generación de humos tóxicos, facilitando las labores de evacuación y protegiendo la integridad estructural del edificio.

El marco normativo nacional español impone una rigurosa estructura técnica y prestacional para garantizar la idoneidad y fiabilidad de estos sistemas de extinción hidráulica. El Código Técnico de la Edificación, en su Documento Básico de Seguridad en caso de Incendio (CTE DB-SI), actúa como la norma marco que define las exigencias mínimas de seguridad en el territorio español, determinando en qué condiciones de uso, altura de evacuación o superficie es obligatoria la instalación de determinados elementos de protección activa. Paralelamente, el Reglamento de Instalaciones de Protección Contra Incendios (RIPCI, aprobado por el Real Decreto 513/2017) gobierna las condiciones de diseño, instalación, mantenimiento preventivo y características de calidad de los componentes de las instalaciones. 

La relevancia técnica de este reglamento radica en que obliga a que todo elemento instalado disponga de una certificación de conformidad con las normas armonizadas europeas. En el caso de las Bocas de Incendio Equipadas con manguera semirrígida (generalmente de diámetro nominal de veinticinco milímetros por su mayor facilidad de manejo), el diseño hidráulico y de componentes se rige por la norma UNE-EN 671-1, que fija los requisitos de caudal mínimo de boquilla en función de la presión dinámica de entrada. Por su parte, la norma de referencia para el diseño, cálculo e instalación de los rociadores automáticos es la UNE-EN 12845, la cual establece de manera pormenorizada las demandas de densidad de diseño (expresada en litros por minuto y metro cuadrado), las áreas de operación de cálculo correspondientes según la clasificación del riesgo (como el Riesgo Ligero o el Riesgo Ordinario) y la autonomía mínima necesaria de la reserva de agua para garantizar una operación hidráulica fiable en condiciones extremas.

Para ilustrar de forma práctica la inserción de estos sistemas dentro del esquema de protección activa, la Figura 1 ofrece un diagrama conceptual de la tipología de las instalaciones de protección contra incendios consideradas. Por su parte, las Figuras 2 y 3 ejemplifican, respectivamente, una Boca de Incendio Equipada en fase de operación manual y un rociador automático activado por su elemento termosensible en una fase autónoma de control de incendio.

### Figuras Técnicas de Apoyo

- **Figura 1**: Contexto general de las instalaciones de protección contra incendios.
  - Ruta en repositorio: `Practica_PCI_LaTeX/Figuras/IPCI.png`
  - Pie de figura: `Fuente: Elaboración grupal.`
- **Figura 2**: Boca de Incendio Equipada de manguera semirrígida en funcionamiento.
  - Ruta en repositorio: `Practica_PCI_LaTeX/Figuras/BIE_en_funcionamiento.png`
  - Pie de figura: `Fuente: Elaboración grupal.`
- **Figura 3**: Rociador automático en funcionamiento por activación termosensible.
  - Ruta en repositorio: `Practica_PCI_LaTeX/Figuras/Rocioador_en_funcionamiento.png`
  - Pie de figura: `Fuente: Elaboración grupal.`

*Nota de portada: Las imágenes `chimenea_recta.jpg`, `ule.jpg` y `escudo-ingenierias.png` quedan documentadas como material de portada o institucional, no como figuras técnicas del cuerpo de la memoria.*

### Objetivos del Proyecto

El objetivo primordial del presente proyecto consiste en capacitar al proyectista en el diseño integral, dimensionamiento hidráulico y verificación reglamentaria de una instalación de protección contra incendios para un edificio residencial colectivo. El enfoque del estudio no se limita a un mero cálculo mecánico, sino que persigue el análisis crítico del comportamiento hidráulico del agua bajo diversas condiciones de demanda simultánea. Para alcanzar este propósito general, se establecen los siguientes objetivos específicos:

- **Diseño geométrico e hidráulico de la red de Bocas de Incendio Equipadas**: Definir el trazado óptimo de las conducciones desde la fuente de suministro común hasta cada uno de los terminales de manguera de veinticinco milímetros distribuidos en la vertical del edificio, garantizando una presión mínima residual y un caudal normalizado en el emisor crítico.
- **Dimensionamiento y distribución del sistema de rociadores automáticos**: Proyectar la red de tuberías de distribución y ramales para dar servicio a los rociadores distribuidos según los criterios de cobertura espacial y densidad de descarga correspondientes a la clasificación del riesgo regulada por la norma UNE-EN 12845.
- **Verificación reglamentaria y simulación en mapa de estados**: Contrastar las variables físicas resultantes del modelo de cálculo (tales como velocidades de circulación por tubería para prevenir fenómenos de erosión y presiones estáticas/dinámicas en los terminales) con las limitaciones impuestas por el Código Técnico de la Edificación y el Reglamento de Instalaciones de Protección Contra Incendios.
- **Optimización y resolución de singularidades**: Evaluar críticamente el sobredimensionamiento derivado de hipótesis voluntarias de protección en contraposición con las exigencias mínimas normativas, y diseñar soluciones de ingeniería de detalle, tales como la incorporación de válvulas reductoras de presión, para corregir sobrepresiones en nudos de cota baja propensos a superar los umbrales de servicio de los materiales.

## Decisión sobre el Carácter Voluntario y Sobredimensionamiento

Tras el análisis preliminar de la tipología del edificio objeto del proyecto, se ha constatado que, de acuerdo con el Código Técnico de la Edificación (DB-SI Sección 4), no existe una obligación reglamentaria de dotar a este tipo de edificio residencial de una instalación completa de Bocas de Incendio Equipadas ni de un sistema de rociadores automáticos. Sin embargo, con el fin de elevar el estándar de seguridad de los ocupantes, el diseño plantea la implantación de ambos sistemas de forma voluntaria. 

A pesar de que el carácter voluntario define gran parte de la filosofía de diseño y justifica el sobredimensionamiento de la reserva de agua del aljibe (calculado para cumplir simultáneamente con los escenarios de BIEs y rociadores), se determina que **la discusión analítica y numérica detallada sobre esta decisión no se incluirá en esta sección de introducción**.

Por coherencia metodológica y para mantener el rigor técnico del documento, este análisis crítico y las justificaciones específicas del dimensionamiento de la reserva de agua se desplazarán al apartado de **Resultados y discusión** (Fase 4) y a las **Conclusiones** (Fase 5). De este modo, la argumentación sobre el sobredimensionamiento y las medidas adoptadas (como el control de sobrepresiones puntuales mediante válvulas reductoras en las plantas inferiores) se basará directamente en los resultados cuantitativos y comprobaciones arrojados por el modelo de simulación hidráulica.

## Control de Cambios y Cierre

- **Estado**: Cerrado y aprobado con ampliación de contenido técnico.
- **Revisión de Coherencia**: Los objetivos han sido expandidos cubriendo de manera explícita el diseño de BIEs, rociadores automáticos, optimización y resolución de singularidades. El contexto y marco normativo han sido desarrollados extensivamente en prosa técnica de alta densidad conceptual, justificando las diferencias y complementariedad de los sistemas manuales y autónomos.
