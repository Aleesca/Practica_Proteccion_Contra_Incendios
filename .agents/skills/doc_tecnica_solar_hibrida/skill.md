---
name: doc_tecnica_solar_hibrida
description: "Guidance on solar thermal systems hybridized with natural gas backup: technical documentation, sizing criteria, hydraulic integration, equipment selection, safety, operation, maintenance, and compliance evidence. Use when the user requests information derived from the project's technical references or says 'escriba segun la doc tecnica'."
---

# Skill: Documentacion Tecnica Solar Hibrida

Esta skill proporciona acceso y guia sobre la documentacion tecnica del proyecto de energia solar termica hibridada con respaldo de gas natural. Cubre datos de partida, criterios de calculo, fuentes normativas, catalogos comerciales, organizacion de evidencias y limites tecnicos.

## Entradas esperadas

- Seccion de memoria o calculo que se quiere documentar.
- Datos disponibles de demanda, energia, potencias, volumen de acumulacion, captadores, intercambiadores, bombas o respaldo de gas natural.
- Fuente concreta a revisar cuando la peticion sea normativa, de catalogo o de trazabilidad.
- Nivel de salida deseado: criterio breve, estructura documental, calculo justificado o revision tecnica.

## Flujo de trabajo

Cuando el usuario solicite informacion tecnica o diga "escriba segun la doc tecnica", sigue estos pasos:

1. Analizar si necesita datos del proyecto, criterio de calculo, normativa, esquema hidraulico, apoyo de catalogo o verificacion documental.
2. Consultar `references/doc_map.md` para localizar la fuente adecuada.
3. Consultar `references/formulario.md` cuando la peticion afecte a formulas, criterios o magnitudes base.
4. Consultar `references/datos_grupo_G1-1.md` cuando la respuesta dependa de datos operativos normalizados.
5. Separar claramente aporte solar, acumulacion, intercambio, bombeo y respaldo de gas natural.
6. Responder con precision, indicando explicitamente la fuente empleada y los datos pendientes.

## Recursos disponibles

- `references/formulario.md`: formulario base y criterios comunes para solar termica, integracion hidraulica y gas natural.
- `references/doc_map.md`: mapa de documentacion y rutas de consulta.
- `references/datos_grupo_G1-1.md`: normalizacion operativa de datos del proyecto.

## Temas cubiertos

- Demanda termica y energia util.
- Captadores solares, rendimiento y superficie de captacion.
- Acumulacion, interacumuladores y volumen de almacenamiento.
- Intercambiadores de calor y circuitos primario/secundario.
- Bombas, caudales, perdidas de carga y control hidraulico.
- Esquema de principio e integracion con respaldo de gas natural.
- Seguridad, ventilacion, evacuacion, normativa y mantenimiento.
- Evidencias para memoria tecnica, calculos, planos y anexos.

## Criterios de salida verificables

- Identifica la fuente usada para cada dato relevante.
- Declara supuestos antes de calcular.
- Indica unidades y condiciones de aplicacion de cada formula.
- Distingue datos medidos, datos de catalogo, normativa y estimaciones.
- Lista riesgos o huecos cuando falten datos de demanda, ubicacion, trazado, equipos o normativa aplicable.

## Integracion con agentes

- Usa `.agents/agents/solar-termica-researcher.md` para investigacion tecnica y trazabilidad documental amplia.
- Usa `latex-writer` solo cuando el contenido tecnico ya este cerrado y deba consolidarse en `Practica_Solar-LaTeX/`.
