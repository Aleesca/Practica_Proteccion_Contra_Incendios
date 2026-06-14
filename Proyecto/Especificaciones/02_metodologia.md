# Especificacion de redaccion: Metodologia

## Objetivo del apartado

Describir como se ha construido el modelo de calculo: datos introducidos, definicion de la topologia del edificio, seleccion del esquema de instalacion, justificacion del trazado y eleccion de equipos y materiales.

## Subapartados propuestos

- Datos introducidos en el programa.
- Topologia del edificio y seleccion del esquema de instalacion.
- Justificacion del trazado elegido.
- Equipos instalados y materiales de la instalacion.

## Contenido definitivo (Cerrado)

### Datos introducidos en el programa

El cálculo de la instalación hidráulica se realiza mediante un modelo numérico en el que se definen los elementos de la red mediante nudos y líneas. Los nudos representan conexiones físicas, derivaciones, cambios de dirección y los puntos terminales de consumo (Bocas de Incendio Equipadas y rociadores automáticos), así como la aspiración del depósito y el grupo de bombeo. Las líneas corresponden a los tramos de tubería caracterizados por su longitud real, material, diámetro nominal y diámetro interior. 

Las bases de diseño hidráulico aplicadas en la simulación del sistema se rigen por coeficientes y parámetros de cálculo normalizados. Para las conducciones, fabricadas en acero al carbono sin soldadura, se define un coeficiente de rugosidad de Hazen-Williams de $C = 120$, conforme a las especificaciones de las tablas de producto y a las prescripciones de la norma UNE-EN 12845. El motor de cálculo del programa procesa las pérdidas de carga lineales basándose en esta formulación hidráulica, la cual es adecuada para fluidos a presión en materiales metálicos. Con el propósito de contabilizar de forma simplificada pero segura las pérdidas de carga secundarias provocadas por las uniones ranuradas, codos, derivaciones y válvulas de corte presentes en la red, se introduce un coeficiente global que incrementa en un 20 % las pérdidas por rozamiento lineal a lo largo de toda la instalación. 

A nivel dinámico, la velocidad máxima del fluido en los tramos se restringe a un límite técnico de 10,0 m/s para prevenir el desgaste erosivo prematuro de las tuberías de acero y evitar fenómenos de inestabilidad hidráulica o golpe de ariete. En cuanto a los terminales de descarga, se configuran dos escenarios operacionales bajo la hipótesis de simultaneidad y clasificación de Riesgo Ordinario 1 (RO1) regulada por la UNE-EN 12845. Esto impone una autonomía mínima de diseño de 60 minutos tanto para el sistema de rociadores como para el de Bocas de Incendio Equipadas. 

Para las Bocas de Incendio Equipadas de manguera semirrígida de veinticinco milímetros de diámetro nominal (BIE 25), el Reglamento de Instalaciones de Protección Contra Incendios y la norma UNE-EN 671-1 establecen una presión residual mínima en boquilla (punta de lanza) de 2,0 bar para asegurar un alcance de chorro y caudal de descarga mínimos efectivos, fijándose asimismo una presión estática máxima de 6,0 bar a la entrada del armario de la BIE para proteger los componentes y garantizar la seguridad de manipulación de los operarios. Cualquier exceso eventual en nudos de cotas bajas del edificio se corrige localmente en obra incorporando válvulas reductoras de presión. 

Para los rociadores automáticos de cobertura extendida (modelo Tyco Series EC-11), la ficha técnica de producto establece una presión mínima residual de funcionamiento de 0,83 bar; sin embargo, debido a las restricciones de redondeo e interfaz en la interfaz gráfica del software de cálculo empleado, este valor se introduce en el modelo con un valor nominal redondeado de 0,8 bar. El volumen de reserva conjunta y el dimensionamiento definitivo de la bomba y el aljibe se determinan a partir de estas restricciones hidráulicas para abastecer la demanda simultánea combinada del área hidráulica de diseño y los puntos de consumo críticos manuales.

El grupo de bombeo y la reserva de agua se calculan para satisfacer la demanda simultánea de los sistemas según las hipótesis de operación: el funcionamiento de las dos Bocas de Incendio Equipadas más desfavorables de forma simultánea y el funcionamiento del área de operación de rociadores definida.

### Topología del edificio y selección del esquema de instalación

El edificio residencial objeto de estudio se compone de un perfil arquitectónico de cinco plantas sobre rasante destinadas a uso de viviendas colectivas y una planta de garaje-aparcamiento subterránea situada en sótano. El esquema hidráulico de protección contra incendios se unifica mediante una red común de alimentación por columna húmeda presurizada, gobernada de manera centralizada por un único grupo de presión de protección contra incendios emplazado en la planta de sótano, contiguo a un depósito o aljibe de reserva de agua común de gran capacidad.

Desde el grupo de bombeo de sótano, el caudal es impulsado en sentido ascendente a través de una columna montante vertical principal de acero al carbono que recorre el patinillo técnico del núcleo común de comunicaciones del edificio. Los diámetros de esta columna montante vertical están calculados y optimizados para atemperar las pérdidas de fricción y el coste material. Así, la montante se inicia en su base con un diámetro nominal de DN40 (40 mm), manteniéndose este diámetro intermedio a lo largo de las plantas de menor cota, y reduciéndose en su tramo superior a un diámetro de DN32 (32 mm) para alimentar las últimas viviendas a cota más elevada. A pesar del estrechamiento superior, la velocidad del fluido en la tubería vertical se estabiliza en un valor máximo de 8,62 m/s ante la demanda combinada extrema, valor que respeta holgadamente el límite de erosión de 10,0 m/s fijado en las bases de cálculo del programa.

A partir de esta columna montante común de distribución vertical, se realizan las derivaciones correspondientes por planta para alimentar de forma selectiva a los sistemas instalados:
1. **Derivaciones de Bocas de Incendio Equipadas (BIE)**: Consisten en derivaciones de diámetro DN32 (diámetro interior de 36,0 mm) que conectan de forma individualizada el colector vertical con los armarios de Bocas de Incendio Equipadas empotrados en las zonas de distribución común (vestíbulos previos o pasillos de acceso a viviendas) de cada planta de cota residencial.
2. **Derivaciones de rociadores automáticos**: Conectan la columna común con una red de distribución horizontal en ramales horizontales de acero que discurren bajo el falso techo de los pasillos comunes y de los interiores de las viviendas, reduciendo progresivamente su diámetro en función de la cercanía a los rociadores terminales individuales para optimizar las velocidades y presiones dinámicas de diseño.

La relación espacial y topológica entre las cotas del edificio, las plantas y las líneas del modelo de cálculo se ilustra con las siguientes figuras de apoyo:
- **Figura 4**: Definición de plantas y cotas del edificio residencial.
  - Archivo en repositorio: `Practica_PCI_LaTeX/Figuras/definicion_plantas.png`
  - Pie de figura: `Fuente: Elaboración grupal.`
- **Figura 5**: Perfil vertical del edificio mostrando la distribución de montantes y cotas de planta.
  - Archivo en repositorio: `Practica_PCI_LaTeX/Figuras/Perfil_Plantas.png`
  - Pie de figura: `Fuente: Elaboración grupal.`

Los planos unifilares de la instalación en tres dimensiones y los detalles de perfil se incorporan en la documentación complementaria adjunta.

### Justificación del trazado elegido

El trazado de la instalación de protección contra incendios se justifica bajo criterios rigurosos de accesibilidad, continuidad hidráulica, simplificación de recorridos físicos y cobertura espacial completa del edificio, garantizando la seguridad en toda la planta construida:
- <u>Trazado de ramales y montantes</u>: La columna montante discurre por patinillos técnicos y conductos verticales comunes en zonas de escaleras y ascensores, lo que facilita las labores de mantenimiento preventivo, inspección visual reglamentaria e independiza los tramos principales del interior de las viviendas. Los ramales de distribución horizontal se canalizan bajo el falso techo desmontable en pasillos y zonas comunes, y a través de falsos techos fijos en las viviendas para no interferir con la estética de las dependencias residenciales.
- <u>Alcance y cobertura de las bocas de incendio</u>: Los armarios de las Bocas de Incendio Equipadas se posicionan estratégicamente en los vestíbulos de distribución común de cada planta, inmediatamente contiguos a las vías de evacuación principales. La ubicación de estos armarios garantiza que, considerando una manguera semirrígida comercial de 30 metros de longitud nominal y un alcance físico proyectado del chorro de agua de lanza de al menos 5 metros (totalizando 35 metros de radio de acción geométrico), se cubra completamente y sin puntos ciegos toda la superficie útil del vestíbulo común, los accesos verticales y las viviendas completas de la planta residencial correspondiente.
- <u>Distribución espacial de la red de rociadores</u>: Los ramales horizontales de rociadores automáticos se ramifican bajo techo para cubrir todas las estancias de las viviendas residenciales. La superficie física total que cuenta con cobertura física protegida mediante la red de rociadores automáticos en la planta residencial es de exactamente \SI{270.88}{\meter\squared} (270,88 m²). Esta superficie física instalada se desglosa geométricamente en dos viviendas simétricas de 127,97 m² de superficie útil de distribución interior cada una, sumado al pasillo común y vestíbulo de acceso que aportan 14,95 m².
- <u>Diferencia entre superficie física y área hidráulica activa</u>: Es fundamental aclarar en términos de ingeniería que esta superficie total protegida de \SI{270.88}{\meter\squared} corresponds al alcance físico constructivo total de las tuberías e inyectores instalados por planta, pero **bajo ninguna circunstancia representa el área de cálculo hidráulica activa**. En el cálculo y simulación hidráulica conforme a la UNE-EN 12845 para Riesgo Ordinario 1 (RO1), el motor del software solo activa simultáneamente el área de operación más desfavorable de rociadores en funcionamiento conjunto (en nuestro modelo, los 3 rociadores críticos activos representados por los nudos 140, 141 y 142). Esto permite dimensionar la bomba de incendios y el volumen de reserva con la máxima demanda de flujo puntual esperada y evitar un sobredimensionamiento desmesurado de la red colectora y grupos activos que harían la instalación inviable económicamente.
- <u>Velocidades de circulación y pérdidas de carga</u>: El diseño hidráulico del trazado evita ramificaciones excesivas y busca recorridos lo más lineales posibles. Los diámetros de los ramales de distribución horizontal se dimensionan de forma decreciente hacia los terminales para equilibrar las pérdidas de carga y estabilizar las velocidades del agua por debajo de los 10,0 m/s admisibles (con un valor pico de 8,62 m/s en la montante reducida y velocidades inferiores en los ramales de viviendas), controlando el desgaste físico y maximizando la presión residual disponible en las boquillas de descarga.

La relación entre el trazado inicial, las derivaciones y los armarios de BIE queda detallada de forma gráfica en la siguiente figura:
- **Figura 6**: Esquema inicial de trazado, tramo y ubicación de Boca de Incendio Equipada.
  - Archivo en repositorio: `Practica_PCI_LaTeX/Figuras/Inicio_Tramo_y_BIE.png`
  - Pie de figura: `Fuente: Elaboración grupal.`

### Equipos instalados y materiales de la instalación

La instalación emplea equipos comerciales homologados y materiales que cumplen con los estándares de fabricación y resistencia exigidos por el RIPCI:
1. **Bocas de Incendio Equipadas (BIE)**:
   - Se selecciona el modelo comercial **IMP Workfire 300/B2** (manguera semirrígida de 25 mm de diámetro y 30 m de longitud).
   - Este equipo cuenta con un racor de conexión roscada, una lanza/boquilla que permite regular el chorro de agua y una válvula de seccionamiento.
   - Dispone de un factor de caudal $K_{BIE} = 42,00$ y una toma adicional de 45 mm para el uso exclusivo de los bomberos. Su montaje se realiza empotrado en la pared del vestíbulo común.
   - Ficha técnica de referencia: `catalogos/ficha_tecnica_BIE.pdf` (incorporada en los anexos).
2. **Rociadores automáticos**:
   - Se adopta el modelo comercial **Tyco Series EC-11** de cobertura extendida (SIN TY5237).
   - Posee un factor de caudal nominal $K = 161,30$ y cuenta con un elemento termosensible (fusible o ampolla de vidrio).
   - La ficha técnica del fabricante establece una presión mínima residual de funcionamiento de **0,83 bar**, la cual se introduce en el software de cálculo como un valor redondeado de **0,8 bar** por limitaciones de la interfaz del software.
   - Ficha técnica de referencia: `catalogos/TFP220_06_2025.pdf` (incorporada en los anexos).
3. **Tuberías de la red**:
   - Se utiliza tubería de acero al carbono estirado sin soldadura.
   - Las uniones se realizan mediante juntas ranuradas y racores homologados.
   - El coeficiente de rugosidad empleado para el cálculo de pérdidas de carga por Hazen-Williams es $C = 120$.

## Control de Cambios y Cierre

- **Estado**: Cerrado y aprobado con ampliación metodológica.
- **Valores y Modelos**: Cruzados y validados contra los catálogos comerciales y la modelización final.
- **Coherencia**: Se mantiene una separación rigurosa. Se describen detalladamente las hipótesis físicas, los coeficientes de fricción y accesorios, y los equipos en prosa continua, eliminando la tabla paramétrica anterior. No se anticipan los caudales específicos de operación ni las presiones de salida calculadas para los puntos críticos de la red, los cuales corresponden a la sección de Resultados.
