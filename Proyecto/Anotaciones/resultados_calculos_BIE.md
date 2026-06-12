<div align="center">

# ANEXO DE CALCULOS

</div>

## Fórmulas Generales

Empiearemos las siguientes:

$$H = Z + (P/\gamma) ; \gamma = \rho \times g ; H_1 = H_2 + h_f$$

Siendo:

$$H = Altura piezométrica, energía por unidad de peso (mca).

z = Cota (m).

P/\gamma = Altura de presión (mca).

\gamma = Peso específico fluido.

\rho = Densidad fluido (kg/m³).

g = Aceleración gravedad. 9,81 m/s².

h_f = Pérdidas de altura piezométrica, energía por unidad de peso (mca).

a) Tuberías y válvulas.

$$H_i - H_j = h_{ij} = r_{ij} \times Q_{ij}^n + m_{ij} \times Q_{ij}^2$$

Darcy - Weisbach :

$$r_{ij} = 10^9 \times 8 \times f \times L \times \rho / (\pi^2 \times g \times D^5 \times 1000) ; n = 2$$

$$m_{ij} = 10^6 \times 8 \times k \times \rho / (\pi^2 \times g \times D^4 \times 1000)$$

Re = 4 x Q / (\pi x D x v)

Re ≤ 2000: Laminar, fórmula de Hagen-Poiseuille: f = 64 / Re

Re ≥ 4000: Turbulento: f = 0.25 / [lg_{10}(\varepsilon / (3.7 x D) + 5.74 / Re^{0.9})]^2

2000 < Re < 4000: Se emplea una interpolación cúbica

Hazen - Williams :

$$r_{ij} = 12,171 \times 10^9 \times L / (C^{1,852} \times D^{4,871}) ; n = 1,852$$

$$m_{ij} = 10^6 \times 8 \times k / (\pi^2 \times g \times D^4)$$

b) Bombas-Grupos de presión.

$$h_{ij} = -\omega^2 x (h_0 - rb \times (Q/\omega)^{nb})$$

Siendo:

f = Factor de fricción en tuberías (adimensional).

L = Longitud equivalente de tubería (m).

D = Diámetro de tubería o válvula (mm).

Q = Caudal (l/s).

\varepsilon = Rugosidad absoluta tubería (mm).

Re = Número de Reynolds (adimensional).

v = Viscosidad cinemática del fluido (m²/s).

k = Coeficiente de pérdidas en válvula (adimensional).

\omega = Coeficiente de velocidad en bombas (adimensional).

h_0 = Altura bomba a caudal cero (mca).

rb = Coeficiente en bombas.

nb = Exponente caudal en bombas.

c) BIES.

$$Q(l/min) = K_{BIE} \times \sqrt{Pma}(bar)$$

$$Q(l/min) = K_{boq} \times \sqrt{Pboq}(bar)$$

$$K_{BIE} = Coeficiente de caudal BIE.$$

$$K_{boq} = Coeficiente de caudal boquilla.

d) Rociador Automático.

Q(I/min) = k x $ \sqrt{P} $ (bar)

## Red IPCI 1

## Datos Generales Instalación

Cálculo por: Hazen - Williams

Pérdidas secundarias: 20 %

Velocidad máxima: 10 m/s

Presión dinámica mínima:

BIE; Pmínima-boquilla(bar): 2 ;Pmáxima-boquilla(bar): 5

HIDRANTE EXTERIOR; Pmínima(bar): 5

ROCIADOR AUTOMATICO; Pmínima(bar):

LIGERO: 0,7 ; ORDINARIO: 0,57 ; EXTRAORDINARIO: 0,5

<div align="center">

Resultados Ramas y Nudos

</div>

<table border="1"><tr><td>Linea</td><td>Nudo Orig.</td><td>Nudo Dest.</td><td>Lreal(m)</td><td>Material</td><td>C</td><td>Q(l/s)</td><td>Dn(mm)</td><td>Dint(mm)</td><td>hf(mca)</td><td>V(m/s)</td></tr><tr><td>7</td><td>8</td><td>9</td><td></td><td>Bomba</td><td></td><td>1,5911</td><td></td><td></td><td>-69,34</td><td></td></tr><tr><td>8</td><td>9</td><td>10</td><td></td><td></td><td></td><td>1,5911</td><td>32</td><td>36</td><td>0,068</td><td>1,56*</td></tr><tr><td>9</td><td>10</td><td>11</td><td>0,38</td><td>Acero</td><td>120</td><td>1,5911</td><td>32</td><td>36</td><td>0,049</td><td>1,56</td></tr><tr><td>10</td><td>14</td><td>7</td><td>3,81</td><td>Acero</td><td>120</td><td>0</td><td>32</td><td>36</td><td>0</td><td>0</td></tr><tr><td>11</td><td>14</td><td>12</td><td>0,16</td><td>Acero</td><td>120</td><td>0</td><td>32</td><td>36</td><td>0</td><td>0</td></tr><tr><td>6</td><td>11</td><td>7</td><td>2,5</td><td>Acero</td><td>120</td><td>1,5911</td><td>32</td><td>36</td><td>0,32</td><td>1,56</td></tr><tr><td>7</td><td>10</td><td>8</td><td>3,81</td><td>Acero</td><td>120</td><td>0</td><td>32</td><td>36</td><td>0</td><td>0</td></tr><tr><td>8</td><td>10</td><td>9</td><td>0,16</td><td>Acero</td><td>120</td><td>0</td><td>32</td><td>36</td><td>0</td><td>0</td></tr><tr><td>9</td><td>13</td><td>11</td><td>3,81</td><td>Acero</td><td>120</td><td>0</td><td>32</td><td>36</td><td>0</td><td>0</td></tr><tr><td>10</td><td>13</td><td>12</td><td>0,16</td><td>Acero</td><td>120</td><td>0</td><td>32</td><td>36</td><td>0</td><td>0</td></tr><tr><td>11</td><td>16</td><td>14</td><td>3,81</td><td>Acero</td><td>120</td><td>0</td><td>32</td><td>36</td><td>0</td><td>0</td></tr><tr><td>12</td><td>16</td><td>15</td><td>0,16</td><td>Acero</td><td>120</td><td>0</td><td>32</td><td>36</td><td>0</td><td>0</td></tr><tr><td>13</td><td>19</td><td>17</td><td>3,81</td><td>Acero</td><td>120</td><td>-1,5911</td><td>32</td><td>36</td><td>0,487</td><td>1,56</td></tr><tr><td>14</td><td>19</td><td>18</td><td>0,16</td><td>Acero</td><td>120</td><td>1,5911</td><td>32</td><td>36</td><td>0,021</td><td>1,56</td></tr><tr><td>15</td><td>7</td><td>8</td><td>2,6</td><td>Acero</td><td>120</td><td>1,5911</td><td>32</td><td>36</td><td>0,332</td><td>1,56</td></tr><tr><td>16</td><td>14</td><td>17</td><td>2,6</td><td>Acero</td><td>120</td><td>1,5911</td><td>32</td><td>36</td><td>0,332</td><td>1,56</td></tr><tr><td>17</td><td>11</td><td>14</td><td>2,6</td><td>Acero</td><td>120</td><td>1,5911</td><td>32</td><td>36</td><td>0,332</td><td>1,56</td></tr><tr><td>18</td><td>8</td><td>11</td><td>2,6</td><td>Acero</td><td>120</td><td>1,5911</td><td>32</td><td>36</td><td>0,332</td><td>1,56</td></tr></table>

<table border="1"><tr><td>Nudo</td><td>Cota(m)</td><td>Factor K</td><td>$\phi$(mm)</td><td>H(mca)</td><td>Pdinám.(mca)</td><td>Pdinám.(bar)</td><td>Pboquilla(bar)</td><td>Caudal(l/s)</td><td>Caudal(l/min)</td></tr><tr><td>8</td><td>0</td><td></td><td></td><td>0</td><td>0</td><td>0</td><td></td><td>-1,591</td><td>-95,466</td></tr><tr><td>9</td><td>0</td><td></td><td></td><td>69,34</td><td>69,34</td><td>6,798</td><td></td><td>0</td><td>0</td></tr><tr><td>10</td><td>0</td><td></td><td></td><td>69,27</td><td>69,272</td><td>6,791</td><td></td><td>0</td><td>0</td></tr><tr><td>11</td><td>0</td><td></td><td></td><td>69,22</td><td>69,223</td><td>6,787</td><td></td><td>0</td><td>0</td></tr><tr><td>12</td><td>4</td><td>42</td><td>BIE 25</td><td>68,9</td><td>64,903</td><td>6,363</td><td></td><td>0</td><td>0</td></tr><tr><td>14</td><td>4</td><td></td><td></td><td>68,9</td><td>64,903</td><td>6,363</td><td></td><td>0</td><td>0</td></tr><tr><td>7</td><td>2,5</td><td></td><td></td><td>68,9</td><td>66,403</td><td>6,51</td><td></td><td>0</td><td>0</td></tr><tr><td>8</td><td>5,1</td><td></td><td></td><td>68,57</td><td>63,471</td><td>6,223</td><td></td><td>0</td><td>0</td></tr><tr><td>9</td><td>6,6</td><td>42</td><td>BIE 25</td><td>68,57</td><td>61,971</td><td>6,076</td><td></td><td>0</td><td>0</td></tr><tr><td>10</td><td>6,6</td><td></td><td></td><td>68,57</td><td>61,971</td><td>6,076</td><td></td><td>0</td><td>0</td></tr><tr><td>11</td><td>7,7</td><td></td><td></td><td>68,24</td><td>60,539</td><td>5,935</td><td></td><td>0</td><td>0</td></tr><tr><td>12</td><td>9,2</td><td>42</td><td>BIE 25</td><td>68,24</td><td>59,039</td><td>5,788</td><td></td><td>0</td><td>0</td></tr><tr><td>13</td><td>9,2</td><td></td><td></td><td>68,24</td><td>59,039</td><td>5,788</td><td></td><td>0</td><td>0</td></tr><tr><td>14</td><td>10,3</td><td></td><td></td><td>67,91</td><td>57,606</td><td>5,648</td><td></td><td>0</td><td>0</td></tr><tr><td>15</td><td>11,8</td><td>42</td><td>BIE 25</td><td>67,91</td><td>56,106</td><td>5,501</td><td></td><td>0</td><td>0</td></tr><tr><td>16</td><td>11,8</td><td></td><td></td><td>67,91</td><td>56,106</td><td>5,501</td><td></td><td>0</td><td>0</td></tr><tr><td>17</td><td>12,9</td><td></td><td></td><td>67,57</td><td>54,674</td><td>5,36</td><td></td><td>0</td><td>0</td></tr><tr><td>18</td><td>14,4</td><td>42</td><td>BIE 25</td><td>67,07</td><td>52,666*</td><td>5,163*</td><td>2</td><td>1,591</td><td>95,466</td></tr><tr><td>19</td><td>14,4</td><td></td><td></td><td>67,09</td><td>52,687</td><td>5,165</td><td></td><td>0</td><td>0</td></tr></table>

NOTA:

- * Rama de mayor velocidad o nudo de menor presión dinámica.

Bomba 7, Caudal (l/s): 1,59; Presión (mca): 69,34

Caudal BIES (l/min): 95,47

Reserva BIES (I): 5.727,96

P mínima BIES-Boquilla (bar): 2 ; Nudo: 18

## Archivos relacionados

- [informe_revision_calculos_bie.md](informe_revision_calculos_bie.md): Auditoría técnica de estos resultados.
- [justificacion_simultaneidad_BIEs.md](justificacion_simultaneidad_BIEs.md): Justificación del cálculo con dos BIEs abiertas.
- [sobre_altura_cotas.md](sobre_altura_cotas.md): Lectura de cotas, nudos y montante vertical.
- [catalogos-bies-rociadores.md](catalogos-bies-rociadores.md): Selección de equipos relacionada con los parámetros hidráulicos.
