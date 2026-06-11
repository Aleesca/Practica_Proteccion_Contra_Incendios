# Formulario base: energia solar termica hibridada con gas natural

## Balance energetico termico

$$ Q_u = m \cdot c_p \cdot \Delta T $$

Donde:
- $Q_u$: energia util requerida [kJ] o [kWh]
- $m$: masa de agua o fluido [kg]
- $c_p$: calor especifico [kJ/(kg K)]
- $\Delta T$: salto termico [K]

Para agua, puede usarse:

$$ Q_u \text{ [kWh]} = \frac{V \cdot \rho \cdot c_p \cdot (T_{uso} - T_{red})}{3600} $$

## Potencia termica

$$ P = \frac{Q_u}{t} $$

Donde:
- $P$: potencia termica [kW]
- $Q_u$: energia util [kWh]
- $t$: tiempo de funcionamiento [h]

## Aporte solar

$$ Q_{solar} = A_c \cdot G \cdot \eta $$

Donde:
- $Q_{solar}$: energia solar util [kWh]
- $A_c$: superficie de captacion [$m^2$]
- $G$: irradiacion incidente en el periodo considerado [$kWh/m^2$]
- $\eta$: rendimiento global del campo solar [-]

Fraccion solar:

$$ f = \frac{Q_{solar}}{Q_{demanda}} $$

## Rendimiento de captador

Forma habitual de catalogo:

$$ \eta = \eta_0 - a_1 \frac{T_m - T_a}{G} - a_2 \frac{(T_m - T_a)^2}{G} $$

Donde:
- $\eta_0$: rendimiento optico [-]
- $a_1$, $a_2$: coeficientes de perdidas del captador
- $T_m$: temperatura media del fluido [C]
- $T_a$: temperatura ambiente [C]
- $G$: irradiancia [$W/m^2$]

Usar esta expresion solo cuando el catalogo facilite coeficientes compatibles.

## Acumulacion

Criterio energetico:

$$ V = \frac{Q_{alm} \cdot 3600}{\rho \cdot c_p \cdot \Delta T} $$

Donde:
- $V$: volumen de acumulacion [$m^3$]
- $Q_{alm}$: energia almacenada [kWh]
- $\rho$: densidad del agua [kg/$m^3$]
- $c_p$: calor especifico [kJ/(kg K)]
- $\Delta T$: salto termico util [K]

Contrastar siempre con recomendaciones de fabricante, normativa y condiciones de uso.

## Intercambiador de calor

$$ P = U \cdot A \cdot \Delta T_{lm} $$

Donde:
- $P$: potencia transferida [W]
- $U$: coeficiente global de transmision [W/($m^2$ K)]
- $A$: superficie de intercambio [$m^2$]
- $\Delta T_{lm}$: diferencia logaritmica media de temperaturas [K]

## Caudal en circuito hidraulico

$$ \dot{m} = \frac{P}{c_p \cdot \Delta T} $$

$$ \dot{V} = \frac{\dot{m}}{\rho} $$

Donde:
- $\dot{m}$: caudal masico [kg/s]
- $\dot{V}$: caudal volumetrico [$m^3/s$]
- $P$: potencia [kW] con unidades coherentes

## Perdida de carga

$$ \Delta p_{total} = \Delta p_{tuberias} + \Delta p_{accesorios} + \Delta p_{equipos} $$

Usar longitudes reales de plano, diametros interiores de catalogo y curvas de bomba verificables. Si no hay datos, declarar el hueco.

## Respaldo de gas natural

Conversion basica con PCS:

$$ Q_{GN} = \frac{P}{PCS \cdot \eta} $$

Donde:
- $Q_{GN}$: caudal de gas natural, con unidades coherentes
- $P$: potencia util requerida
- $PCS$: poder calorifico superior del gas natural
- $\eta$: rendimiento del equipo auxiliar

Datos de referencia disponibles en `00_Data/datos_GN.md`:
- PCS: 40.68 MJ/$m^3(s)$
- Potencias auxiliares: caldera, cocina, horno y secadora

## Criterios de documentacion

- Indicar siempre fuente, unidades y condicion de uso.
- Separar calculo solar, calculo hidraulico y calculo de respaldo de gas natural.
- No reutilizar criterios de otros combustibles para gas natural sin justificacion normativa.
- Declarar como pendiente cualquier demanda, temperatura, rendimiento, longitud o dato de catalogo no encontrado.
