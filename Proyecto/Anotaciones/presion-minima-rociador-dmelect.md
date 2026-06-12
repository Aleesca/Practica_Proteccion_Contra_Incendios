# Presión mínima residual del rociador para DMELECT

## 1. Datos de partida

Rociador comercial seleccionado:

- **Identificación:** RA2845.
- **Tipo:** rociador colgante de respuesta rápida, cobertura extendida y riesgo ligero.
- **Factor K:** 5,6 imperial / **80 métrico** \($L/min/\sqrt{bar}$\).
- **Orificio nominal / diámetro de boquilla:** 1/2" (**15 mm**).
- **Rosca:** 1/2" NPT (R1/2).

Fuente: `00_Data/Selecciones_comerciales/Rociador_RA2845.pdf`.

---

## 2. Presión mínima residual según ficha técnica

La ficha técnica da la siguiente tabla de área de cobertura:

| Caudal | Presión residual | Área máxima |
| :--- | :--- | :--- |
| 26 gpm / 98,4 L/min | **21,6 psi / 1,5 bar** | 16 ft x 16 ft / 4,9 m x 4,9 m |
| 33 gpm / 125,0 L/min | 34,7 psi / 2,4 bar | 18 ft x 18 ft / 5,5 m x 5,5 m |
| 40 gpm / 151,4 L/min | 51,0 psi / 3,5 bar | 20 ft x 20 ft / 6,0 m x 6,0 m |

Por tanto, si en DMELECT se introduce el dato comercial mínimo de la ficha:

> **Presión mínima residual = 1,5 bar**

Este valor corresponde al primer punto listado por el fabricante para cobertura extendida de riesgo ligero.

---

## 3. Comprobación hidráulica por factor K

Relación hidráulica del rociador:

```text
Q = K * sqrt(P)
P = (Q / K)^2
```

Donde:

- `Q` = caudal del rociador en L/min.
- `K` = 80 L/min/sqrt(bar).
- `P` = presión residual en bar.

Para el punto mínimo de ficha:

```text
P = (98,4 / 80)^2
P = 1,51 bar
```

El cálculo confirma el valor de ficha:

> **P ≈ 1,5 bar**

---

## 4. Criterios normativos consultados en NotebookLM

Consulta realizada en el notebook `PCI_Practicas`, fuente interna UNE-EN 12845:2016+A1:2021:

- **Separación mínima entre rociadores:** 2,0 m, salvo medidas para impedir mojado mutuo.
- **Riesgo Ligero (RL), rociadores de techo estándar:** superficie máxima 21,0 m² y separación máxima 4,6 m.
- **Riesgo Ordinario (RO), rociadores de techo estándar:** superficie máxima 12,0 m² y separación máxima 4,0 m.
- **Distancia máxima a paredes y particiones:** el menor valor aplicable; para separación normal, 2,0 m.
- Los rociadores residenciales y de cobertura ampliada se tratan como tecnología especial; deben justificarse con la ficha, ensayos/aprobaciones del fabricante o desviación documentada con nivel de protección equivalente.

Por tanto, las coberturas comerciales de **4,9 x 4,9 m**, **5,5 x 5,5 m** y **6,0 x 6,0 m** no deben tratarse como rociadores estándar UNE-EN 12845 sin justificar su condición de cobertura ampliada.

---

## 5. Comparación de opciones comerciales

Si el rociador se calcula como Riesgo Ordinario 1 (RO1) con densidad de diseño:

```text
Densidad = 5,0 mm/min = 5,0 L/min·m²
Q = densidad * área cubierta
P = (Q / K)^2
```

Para el área de cobertura mínima listada por ficha:

```text
Área = 4,9 * 4,9 = 24,01 m²
Q = 5,0 * 24,01 = 120,05 L/min
P = (120,05 / 80)^2 = 2,25 bar
```

Resultado:

> **Presión residual para RO1 con 4,9 m x 4,9 m = 2,25 bar**

Para referencia, si se aplicase la misma densidad RO1 a las otras áreas listadas:

| Área cubierta | Superficie | Caudal RO1 requerido | Presión con K=80 |
| :--- | ---: | ---: | ---: |
| 4,9 m x 4,9 m | 24,01 m² | 120,05 L/min | **2,25 bar** |
| 5,5 m x 5,5 m | 30,25 m² | 151,25 L/min | **3,57 bar** |
| 6,0 m x 6,0 m | 36,00 m² | 180,00 L/min | **5,06 bar** |

Aunque un único rociador de 6,0 m x 6,0 m podría cubrir por superficie una estancia de 34,06 m², exige una presión residual muy alta y aleja el diseño de las separaciones estándar. La opción **4,9 m x 4,9 m** es la más equilibrada porque:

- Es la cobertura comercial más próxima a la separación estándar RL de 4,6 m.
- Reduce presión residual frente a las opciones 5,5 m y 6,0 m.
- Favorece una distribución más segura, con menores distancias reales hasta el foco de incendio.
- Aumenta el número de rociadores en alguna estancia, pero puede reducir la exigencia sobre bomba y tuberías frente a forzar una cobertura mayor.

---

## 6. Cálculo para las dos áreas de vivienda

Áreas de vivienda indicadas:

- Área A: **34,06 m²**.
- Área B: **22,489 m²**.

Criterio adoptado: usar el punto comercial **4,9 m x 4,9 m**, con caudal de ficha **98,4 L/min** y presión comercial mínima **1,5 bar**. Es el punto más eficiente entre seguridad y economía.

### 6.1. Área A: 34,06 m²

No se recomienda resolver esta estancia con un único rociador de 6,0 m x 6,0 m, aunque la superficie de 36,00 m² lo permita en ficha. Para equilibrar seguridad, separación y presión, se adoptan **2 rociadores** con cobertura 4,9 m x 4,9 m.

```text
Área por rociador = 34,06 / 2 = 17,03 m²
Q_RO1 = 5,0 * 17,03 = 85,15 L/min
P_RO1 = (85,15 / 80)^2 = 1,13 bar
```

Como la presión por densidad RO1 queda por debajo del mínimo comercial listado para el punto 4,9 m x 4,9 m:

> **Presión mínima residual a introducir: 1,5 bar por rociador**

Caudal de comprobación:

```text
Caudal mínimo por ficha = 98,4 L/min por rociador
Caudal total con 2 rociadores = 196,8 L/min
```

### 6.2. Área B: 22,489 m²

La estancia queda dentro de la cobertura comercial 4,9 m x 4,9 m:

```text
Área comercial 4,9 x 4,9 = 24,01 m²
Área real = 22,489 m²
```

Con 1 rociador:

```text
Q_RO1 = 5,0 * 22,489 = 112,45 L/min
P_RO1 = (112,45 / 80)^2 = 1,98 bar
```

Como la presión por densidad RO1 supera el mínimo comercial de 1,5 bar:

> **Presión mínima residual a introducir: 1,98 bar**

Si se exigiera cumplimiento estricto de la tabla estándar RL de UNE-EN 12845 sin justificar cobertura ampliada, esta estancia supera 21,0 m² y habría que estudiar 2 rociadores o ajustar la geometría de cobertura. Con cobertura ampliada justificada por ficha, 1 rociador es la solución más económica.

---

## 7. Resumen para DMELECT

Para introducir el dato comercial del rociador según la ficha técnica:

> **Presión mínima residual: 1,5 bar**

Para las dos áreas reales de vivienda, usando cobertura comercial 4,9 m x 4,9 m:

| Zona | Área | Rociadores recomendados | Área por rociador | Presión mínima residual DMELECT | Criterio |
| :--- | ---: | ---: | ---: | ---: | :--- |
| Área A | 34,06 m² | 2 | 17,03 m² | **1,5 bar** | Mínimo comercial de ficha gobierna |
| Área B | 22,489 m² | 1 | 22,489 m² | **1,98 bar** | Densidad RO1 gobierna |

Conclusión práctica:

- La cobertura más factible y eficiente es **4,9 m x 4,9 m**.
- Para **34,06 m²**, usar **2 rociadores** y **1,5 bar** por rociador.
- Para **22,489 m²**, usar **1 rociador** y **1,98 bar**.
- La colocación final debe verificarse sobre plano: separación mínima entre rociadores **≥ 2,0 m** y distancia a paredes conforme a la justificación aplicable. Con UNE-EN 12845 estándar, la distancia normal a pared queda limitada a **2,0 m**; con cobertura ampliada, debe quedar respaldada por ficha/aprobación del fabricante.
