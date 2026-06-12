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

## 6. Cálculo por estancia de la vivienda

Áreas tomadas de `Proyecto/Anotaciones/areas.md`:

- Zona común: **14,952 m²**.
- Salón: **34,060 m²**.
- Cocina: **10,745 m²**.
- Pasillo: **17,325 m²**.
- Cuarto de servicios con baño incluido: **12,079 m²**.
- Escritorio: **9,430 m²**.
- Dormitorio (2 camas): **11,149 m²**.
- Dormitorio principal: **21,963 m²**.

Criterio adoptado:

- Mantener el mismo rociador en toda la vivienda: **boquilla 15 mm** y **K = 80**.
- Usar el punto comercial más eficiente: **4,9 m x 4,9 m**, área máxima **24,01 m²**.
- Número de rociadores por estancia: `ceil(area / 24,01)`.
- Presión DMELECT por estancia: el mayor valor entre la presión calculada por densidad RO1 y el mínimo comercial de ficha **1,5 bar**.

Fórmulas:

```text
N = ceil(Área estancia / 24,01)
Área por rociador = Área estancia / N
Q_RO1 = 5,0 * Área por rociador
P_RO1 = (Q_RO1 / 80)^2
P_DMELECT = max(P_RO1, 1,5 bar)
```

### 6.1. Tabla de cálculo

| Estancia | Área | Rociadores | Área por rociador | Q_RO1 | P_RO1 | Presión mínima DMELECT |
| :--- | ---: | ---: | ---: | ---: | ---: | ---: |
| Zona común | 14,952 m² | 1 | 14,952 m² | 74,76 L/min | 0,87 bar | **1,50 bar** |
| Salón | 34,060 m² | 2 | 17,030 m² | 85,15 L/min | 1,13 bar | **1,50 bar** |
| Cocina | 10,745 m² | 1 | 10,745 m² | 53,73 L/min | 0,45 bar | **1,50 bar** |
| Pasillo | 17,325 m² | 1 | 17,325 m² | 86,63 L/min | 1,17 bar | **1,50 bar** |
| Cuarto de servicios con baño incluido | 12,079 m² | 1 | 12,079 m² | 60,40 L/min | 0,57 bar | **1,50 bar** |
| Escritorio | 9,430 m² | 1 | 9,430 m² | 47,15 L/min | 0,35 bar | **1,50 bar** |
| Dormitorio (2 camas) | 11,149 m² | 1 | 11,149 m² | 55,75 L/min | 0,49 bar | **1,50 bar** |
| Dormitorio principal | 21,963 m² | 1 | 21,963 m² | 109,82 L/min | 1,88 bar | **1,88 bar** |

### 6.2. Interpretación

El **diámetro de boquilla se mantiene igual en todas las estancias** porque se usa el mismo rociador:

- Orificio nominal / diámetro de boquilla: **1/2" (15 mm)**.
- Factor K: **80**.
- Rosca: **1/2" NPT (R1/2)**.

La presión mínima no cambia el diámetro de la boquilla; solo representa la presión residual necesaria para que ese mismo rociador descargue el caudal requerido.

Con el criterio de cálculo por densidad RO1, la única estancia que supera el mínimo comercial de **1,5 bar** es el **Dormitorio principal**, con **1,88 bar**. Si se adopta exclusivamente el punto comercial de ficha para cobertura ampliada 4,9 m x 4,9 m, se puede mantener **1,5 bar uniforme** para los rociadores de vivienda, siempre que se documente esa justificación comercial y ningún rociador supere los **24,01 m²** de cobertura.

---

## 7. Resumen para DMELECT

Para todos los rociadores de vivienda:

- **Modelo único:** RA2845.
- **Boquilla:** 15 mm.
- **Factor K:** 80.
- **Cobertura comercial adoptada:** 4,9 m x 4,9 m.

Presiones mínimas a introducir por estancia si se calcula con densidad RO1:

| Estancia | Presión mínima residual |
| :--- | ---: |
| Zona común | **1,50 bar** |
| Salón | **1,50 bar** |
| Cocina | **1,50 bar** |
| Pasillo | **1,50 bar** |
| Cuarto de servicios con baño incluido | **1,50 bar** |
| Escritorio | **1,50 bar** |
| Dormitorio (2 camas) | **1,50 bar** |
| Dormitorio principal | **1,88 bar** |

Conclusión práctica:

- Para mantener el mismo diámetro de boquilla, lo decisivo es usar el mismo rociador **K=80 / 15 mm** en todas las estancias.
- Si se quiere una entrada uniforme en DMELECT basada en ficha comercial, usar **1,5 bar** para vivienda completa.
- Si se quiere recoger la comprobación por densidad RO1 estancia a estancia, usar **1,88 bar** en el dormitorio principal y **1,5 bar** en el resto.
- El salón requiere **2 rociadores** por superar los 24,01 m² de cobertura del punto 4,9 m x 4,9 m.
- La colocación final debe verificarse sobre plano: separación mínima entre rociadores **≥ 2,0 m** y distancia a paredes conforme a la justificación aplicable. Con UNE-EN 12845 estándar, la distancia normal a pared queda limitada a **2,0 m**; con cobertura ampliada, debe quedar respaldada por ficha/aprobación del fabricante.

## Archivos relacionados

- [areas.md](areas.md): Superficies por estancia utilizadas en la tabla de cálculo.
- [superficie-rociadores.md](superficie-rociadores.md): Clase de riesgo, densidad de diseño y cobertura máxima.
- [catalogos-bies-rociadores.md](catalogos-bies-rociadores.md): Identificación del modelo RA2845 y parámetros del rociador.
- [justificacion_economica_rociador_unico.md](justificacion_economica_rociador_unico.md): Motivo técnico-económico para mantener un único modelo.
- [sobre_altura_cotas.md](sobre_altura_cotas.md): Relación entre presión residual y asignación vertical de nudos.
