# Presión mínima residual del rociador para DMELECT (Modelo Tyco K160)

## 1. Datos de partida

Rociador comercial unificado seleccionado (Homologado y distribuido en España/Europa):

- **Fabricante:** Tyco Fire Protection Products (Johnson Controls España).
- **Modelo:** Tyco Series EC-11 (Pendent Extended Coverage).
- **SIN:** TY5237.
- **Tipo:** Rociador colgante de respuesta rápida/estándar y cobertura extendida para **Riesgo Ordinario (ECOH)**.
- **Factor K:** **161,3 métrico** ($L/min/\sqrt{bar}$) / 11,2 imperial.
- **Orificio nominal:** 3/4" NPT (DN20).
- **Certificaciones / Homologaciones:** Marcado CE, cULus Listed, FM Approved para Riesgo Ordinario.
- **Ficha Técnica Oficial (Data Sheet):** TFP220.
- **Página Web de Tyco:** [Tyco Fire Products](https://www.tyco-fire.com/)
- **Portal de Documentación Oficial:** [Tyco Datasheet TFP220](https://docs.jci.com/tycofire/tfp220)

---

## 2. Presión mínima residual según norma y ficha (OH1 / RO1)

La ficha técnica oficial del fabricante (TFP220, Design Criteria) certifica los requisitos hidráulicos para cumplimiento de densidad en **Ordinary Hazard (Riesgo Ordinario - RO1)**:

| Cobertura (m x m) | Cobertura (ft x ft) | Caudal Requerido (U.S. GPM / L/min) | **Presión Residual Mínima (psi / bar)** |
| :--- | :--- | :--- | :--- |
| **4,9 m x 4,9 m** | **16 ft x 16 ft** (24,01 m²) | **39 GPM** (147,6 L/min) | **12,1 psi** (0,83 bar ≈ 0,8 bar) |
| 5,5 m x 5,5 m | 18 ft x 18 ft (30,25 m²) | 46 GPM (174,1 L/min) | 16,9 psi (1,17 bar) |
| 6,1 m x 6,1 m | 20 ft x 20 ft (37,21 m²) | 56 GPM (212,0 L/min) | 25,0 psi (1,72 bar) |

Dato a introducir en DMELECT:

> **Presión mínima residual = 0,8 bar** (aproximación comercial de los 0,83 bar nominales de ficha)

Este valor garantiza la densidad de diseño superior a 5,0 mm/min exigida por la **UNE-EN 12845** para Riesgo Ordinario utilizando tecnología de cobertura ampliada.

---

## 3. Comprobación hidráulica por factor K (Métrico)

Relación hidráulica:
```text
Q = K * sqrt(P)
P = (Q / K)^2
```

Para el punto de diseño de ficha (147,6 L/min con K=161,3):
```text
P = (147,6 / 161,3)^2
P = (0,9151)^2
P = 0,837 bar ≈ 0,8 bar (12,1 psi)
```

Este cálculo confirma matemáticamente la consistencia del factor K métrico (161,3) con la presión de 0,83 bar declarada por el fabricante para el caudal de 147,6 L/min.

---

## 4. Justificación Normativa UNE-EN 12845

Al ser un fabricante internacional líder plenamente establecido en España a través de Johnson Controls / Tyco Fire Protection Products, el **Tyco TY5237** se integra perfectamente en la justificación del **Anexo L** (Tecnología Especial) de la norma española:
1.  **Densidad:** El caudal de 147,6 L/min sobre la cobertura real de 24,01 m² proporciona una densidad real de **6,14 mm/min**, superando los **5,0 mm/min** mínimos exigidos por la UNE-EN 12845 para RO1.
2.  **Marcado CE y RIPCI:** Cuenta con marcado CE reglamentario y homologación cULus/FM para su aplicación en Riesgo Ordinario, cumpliendo las exigencias del RIPCI (RD 513/2017) para equipos comercializados en el mercado español.
3.  **Alineación Normativa:** La tecnología de cobertura ampliada bajo el Anexo L de la UNE-EN 12845 permite optimizar la distribución de rociadores manteniendo la legalidad técnica mediante ensayos certificados del fabricante.

---

## 5. Resumen para DMELECT

Para todos los rociadores de la instalación (RO1):

- **Modelo único:** Tyco Series EC-11 (SIN TY5237).
- **Factor K:** 161,3 (11,2 imperial).
- **Presión mínima residual:** **0,8 bar** (0,83 bar nominal).
- **Cobertura comercial adoptada:** 4,9 m x 4,9 m.

---

## 6. Archivos relacionados

- [catalogos-bies-rociadores.md](catalogos-bies-rociadores.md): Datos y enlaces de catálogos de BIEs y rociadores.
- [coberturas_limites_rociadores.md](coberturas_limites_rociadores.md): Validación legal bajo UNE-EN 12845.
- [justificacion_economica_rociador_unico.md](justificacion_economica_rociador_unico.md): Ventajas del rociador unificado y ahorro hidráulico.
