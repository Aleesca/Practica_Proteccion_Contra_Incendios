# Datos normalizados del proyecto

## Datos comunes

- Dominio del proyecto: energia solar termica hibridada con respaldo de gas natural.
- Ubicacion de referencia: Leon, salvo que otra fuente del proyecto indique lo contrario.
- Salida editorial: `Practica_Solar-LaTeX/`.
- Plano y modelos de apoyo: `00_Instalacion_hibrida/` y `00_Plano/`.
- Datos de gas natural normalizados: `00_Data/datos_GN.md`.

## Respaldo de gas natural

| Parametro | Valor | Unidad | Fuente |
| --- | ---: | --- | --- |
| Potencia caldera | 22 | kW | `00_Data/datos_GN.md` |
| Potencia cocina | 5 | kW | `00_Data/datos_GN.md` |
| Potencia horno | 12 | kW | `00_Data/datos_GN.md` |
| Potencia secadora | 11.3 | kW | `00_Data/datos_GN.md` |
| PCS gas natural | 40.68 | MJ/m3(s) | `00_Data/datos_GN.md` |

## Equipos y subsistemas a documentar

- Captadores solares termicos.
- Soportes y montaje en cubierta.
- Deposito de acumulacion o interacumulador bivalente.
- Intercambiadores de calor.
- Bombas de circulacion.
- Circuito primario, circuito secundario y conexion con apoyo de gas natural.
- Sistema de regulacion, seguridad, llenado, purga y mantenimiento.

## Fuentes de datos de equipo

- Captadores: `00_Data/Catalogos_comerciales/Captadores/`.
- Acumulacion: `00_Data/Catalogos_comerciales/Interacumuladores_ACS_bivalentes/`.
- Criterios de instalacion: manuales Baxi en `00_Data/`.
- Normativa de gas natural: `00_Data/Normativa_Gas_Natural/`.

## Observaciones

- Las demandas de ACS, perfiles de uso, superficie de captacion, volumen de acumulacion y trazados deben tomarse de las fuentes del proyecto o declararse como dato pendiente.
- Las distancias, longitudes y ubicaciones deben medirse sobre planos verificables.
- Los criterios de gas natural no sustituyen los criterios solares: solo gobiernan el subsistema auxiliar y su instalacion receptora.
