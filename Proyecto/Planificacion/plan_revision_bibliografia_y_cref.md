# Plan: Revision de Bibliografia y Referencias Cruzadas con cleveref

> Source PRD: solicitud de revision sobre `Practica_PCI_LaTeX/main.tex` para integrar referencias bibliograficas y adaptar las referencias cruzadas hacia figuras, anejos y otros elementos mediante `\cleveref{}` / `\cref{}`.

## Decisiones arquitectonicas

Decisiones duraderas que deben mantenerse durante toda la revision:

- **Motor bibliografico**: mantener `biblatex` con `backend=biber`, `style=ieee` y `sorting=none`, ya cargado en el preambulo.
- **Archivo de bibliografia**: usar `Practica_PCI_LaTeX/refs.bib` como fuente unica de claves bibliograficas para la memoria.
- **Fuentes de contraste locales**: revisar obligatoriamente `Proyecto/Anotaciones/` para extraer enlaces web, referencias normativas, fichas tecnicas y menciones a fuentes ya usadas durante el desarrollo del proyecto.
- **Fuente NotebookLM**: invocar `nlm-skill` para conectar con el notebook `PCI_Practica`, listar o consultar sus fuentes y recopilar la normativa efectivamente empleada en el proyecto antes de cerrar `refs.bib`.
- **Formato bibliografico normativo**: las normas y reglamentos deben registrarse con formato propio de normativa tecnica en estilo IEEE, sin fechas de acceso (`urldate`) y sin enlaces web (`url`). Los enlaces localizados en anotaciones o NotebookLM sirven para identificar la fuente, no para imprimirlos en la bibliografia final.
- **Activacion en LaTeX**: reactivar `\addbibresource{refs.bib}` en el preambulo del documento principal y `\printbibliography[title={Bibliografia}]` antes de los anejos.
- **Referencias cruzadas**: usar `\cref{}` para referencias en mitad de frase y `\Cref{}` al inicio de frase. Sustituir las formas manuales `Figura~\ref{...}`, `Figuras~\ref{...}` y menciones textuales a anexos por referencias inteligentes.
- **Nomenclatura de anejos**: mantener el contador personalizado `appendixcounter` y la configuracion de `\crefname{appendixcounter}{Anexo}{Anexos}`. Incorporar etiquetas estables a todos los anejos que se referencien desde el cuerpo.
- **Alcance de la revision**: no reescribir el contenido tecnico salvo lo necesario para insertar citas, mejorar trazabilidad documental y adaptar la redaccion a las referencias cruzadas.

---

## Contexto detectado

- `main.tex` tiene comentado `\addbibresource{refs.bib}` al inicio del documento.
- La impresion de bibliografia esta comentada al final de la memoria, antes de los anejos.
- `preamble.sty` ya carga `biblatex`, `hyperref` y `cleveref` en un orden adecuado.
- `refs.bib` contiene actualmente referencias de instalaciones de gas, por lo que no representa aun la bibliografia real de la practica de proteccion contra incendios.
- `Proyecto/Anotaciones/` contiene enlaces y menciones documentales que deben auditarse antes de redactar `refs.bib`: DMELECT, Tyco/JCI, catalogos IMP, CTE DB-SI, RIPCI, UNE-EN 671-1, UNE-EN 12845 y documentos de apoyo sobre BIEs y rociadores.
- Algunas anotaciones citan fuentes web como ayuda de trabajo; esas URLs no deben trasladarse automaticamente a la bibliografia final cuando la fuente sea una norma o reglamento.
- Existen referencias manuales a figuras en el cuerpo, por ejemplo `Figura~\ref{fig:ipci}`, `Figuras~\ref{fig:bie_fun} y~\ref{fig:rociador_fun}`, `Figura~\ref{fig:def_plantas}`, `Figura~\ref{fig:perfil_plantas}` y `Figura~\ref{fig:inicio_tramos}`.
- Los anejos de calculos y planos ya tienen etiquetas (`anex:calculos`, `anex:planos`), pero el anejo de caracteristicas tecnicas no tiene una etiqueta propia.
- Hay menciones textuales a anexos y fichas tecnicas que deben convertirse en referencias trazables, especialmente en la seleccion de equipos comerciales y en el cierre de conclusiones.

---

## Fase 1: Auditoria de `Proyecto/Anotaciones/`

**Historias cubiertas**: como autor, necesito localizar todas las fuentes ya usadas durante el trabajo; como revisor, necesito distinguir entre enlaces de consulta, normativa aplicable y documentos comerciales citables.

### Que construir

Revisar todos los Markdown de `Proyecto/Anotaciones/` buscando enlaces web, menciones normativas y referencias a fichas tecnicas. El resultado debe ser un inventario operativo que separe normativa, catalogos/fichas de fabricante, manuales de software y enlaces auxiliares que no deben aparecer en bibliografia.

### Criterios de aceptacion

- [ ] Se revisan todas las anotaciones, no solo las que ya parecen normativas.
- [ ] Se identifican los enlaces web usados como fuente de trabajo, incluidos DMELECT, Tyco/JCI, IMP, BOE/CTE y documentos tecnicos externos.
- [ ] Se clasifican las fuentes en normativa/reglamento, ficha tecnica/catalogo, manual de software y apoyo web no bibliografico.
- [ ] Las fuentes normativas detectadas en anotaciones se contrastan con NotebookLM antes de cerrar `refs.bib`.
- [ ] Las URLs de normas y reglamentos no se trasladan como `url` ni `urldate` a la bibliografia final.

---

## Fase 2: Consulta del notebook `PCI_Practica` con `nlm-skill`

**Historias cubiertas**: como autor, necesito recopilar la normativa empleada desde el cuaderno documental del proyecto; como revisor, necesito que la bibliografia final proceda de las fuentes reales del notebook y no de una lista inferida.

### Que construir

Invocar `nlm-skill` y conectar con el notebook `PCI_Practica`. El flujo previsto es comprobar autenticacion, localizar el notebook, listar sus fuentes y realizar una consulta puntual para extraer toda la normativa y documentacion tecnica usada en la practica. No se debe usar el chat interactivo; se debe usar una consulta automatizada de una sola respuesta.

### Criterios de aceptacion

- [ ] Se ejecuta o se documenta el paso `nlm login --check` antes de consultar NotebookLM.
- [ ] Se localiza el notebook `PCI_Practica` mediante `nlm notebook list` o alias existente.
- [ ] Se lista el conjunto de fuentes del notebook con `nlm source list <notebook>`.
- [ ] Se consulta el notebook con una pregunta orientada a recopilar normativa: CTE DB-SI, RIPCI/RD 513/2017, UNE-EN 671-1, UNE-EN 12845 y cualquier otra fuente normativa usada en el proyecto.
- [ ] La respuesta de NotebookLM se cruza con `Proyecto/Anotaciones/` y con los PDFs locales de `Normativa/`.
- [ ] No se incorporan fuentes al `refs.bib` solo porque aparezcan en una web si no estan respaldadas por el notebook, las anotaciones o los documentos locales del proyecto.

---

## Fase 3: Inventario bibliografico minimo viable

**Historias cubiertas**: como lector de la memoria, necesito que cada afirmacion normativa o documental relevante tenga una fuente identificable; como revisor, necesito que `refs.bib` contenga referencias de PCI y no de otro proyecto.

### Que construir

Sustituir o ampliar el contenido de `refs.bib` con un conjunto minimo de entradas pertinentes para la practica, usando como entradas de trabajo `Proyecto/Anotaciones/`, el notebook `PCI_Practica` y los PDFs locales de normativa. La primera version debe cubrir, como minimo, CTE DB-SI, RIPCI, UNE-EN 671-1, UNE-EN 12845, ficha tecnica de la BIE comercial, ficha tecnica del rociador Tyco EC-11 y documentacion del software o criterio de calculo usado si se cita en la memoria.

### Criterios de aceptacion

- [ ] `refs.bib` no contiene referencias heredadas de gas salvo que se justifique expresamente su uso.
- [ ] Cada entrada tiene una clave estable, legible y especifica, por ejemplo `CTE_DBSI`, `RIPCI_2017`, `UNE_EN_671_1`, `UNE_EN_12845`, `TYCO_EC11` o equivalente.
- [ ] Las normas UNE se documentan como normativa tecnica, no como paginas web.
- [ ] Las entradas normativas no contienen `url`, `urldate` ni fechas de acceso.
- [ ] Los reglamentos publicados oficialmente se formatean como disposiciones reglamentarias o normativa, no como enlaces web.
- [ ] Las fichas tecnicas comerciales quedan citables desde la seleccion de equipos y coherentes con los PDFs anexados.
- [ ] No se introducen claves duplicadas ni campos bibliograficos incompatibles con `biblatex`.

---

## Fase 4: Activacion controlada de bibliografia

**Historias cubiertas**: como autor, necesito que las citas se compilen; como lector, necesito una seccion final de bibliografia visible en el indice y antes de los anejos.

### Que construir

Reactivar la conexion entre `main.tex` y `refs.bib`, y habilitar la impresion de la bibliografia antes de la secuencia de anejos. Mantener el titulo `Bibliografia` y revisar si la entrada al indice debe ser manual o ya queda cubierta por la configuracion de `biblatex`.

### Criterios de aceptacion

- [ ] `\addbibresource{refs.bib}` esta activo y apunta al archivo correcto.
- [ ] `\printbibliography[title={Bibliografia}]` esta activo antes del primer `\myappendix`.
- [ ] La bibliografia aparece antes de `Anexo 1. Caracteristicas tecnicas`.
- [ ] La entrada de bibliografia en el indice no queda duplicada.
- [ ] El flujo de compilacion previsto incluye `pdflatex`, `biber`, `pdflatex`, `pdflatex` o el equivalente configurado en el editor.

---

## Fase 5: Insercion de citas en la redaccion tecnica

**Historias cubiertas**: como revisor tecnico, necesito verificar rapidamente que las afirmaciones normativas y de catalogo no son solo declarativas; como lector, necesito distinguir entre criterios normativos, datos de fabricante y decisiones de proyecto.

### Que construir

Insertar citas bibliograficas en los puntos donde la memoria invoca normativa, requisitos de producto, autonomia, presiones, caudales, clasificacion de riesgo o documentacion comercial. Las citas deben integrarse en prosa sin saturar cada frase; basta con citar al cerrar bloques de contenido que proceden de una misma fuente.

### Criterios de aceptacion

- [ ] La descripcion del marco normativo cita CTE DB-SI, RIPCI, UNE-EN 671-1 y UNE-EN 12845.
- [ ] La metodologia cita la fuente de criterios de presion, autonomia, rugosidad o limites cuando proceda.
- [ ] La seleccion de BIE y rociador cita las fichas tecnicas de fabricante correspondientes.
- [ ] La verificacion normativa cita las fuentes al presentar los criterios de aceptacion, no solo al final del documento.
- [ ] No hay citas huerfanas: toda clave usada en `main.tex` existe en `refs.bib`.
- [ ] No hay entradas bibliograficas sin uso salvo fuentes deliberadamente conservadas para revision posterior.

---

## Fase 6: Normalizacion de referencias a figuras con `\cref{}`

**Historias cubiertas**: como lector, quiero que las referencias a figuras sean uniformes, enlazables y resistentes a cambios de numeracion; como autor, quiero evitar escribir manualmente "Figura" o "Figuras" en cada caso.

### Que construir

Sustituir referencias manuales a figuras por `\cref{}` o `\Cref{}`. Cuando se referencien varias figuras juntas, agrupar las claves en una sola llamada de `cleveref` siempre que la redaccion lo permita.

### Criterios de aceptacion

- [ ] `Figura~\ref{fig:ipci}` se convierte en una referencia con `\cref{fig:ipci}` o `\Cref{fig:ipci}` segun posicion gramatical.
- [ ] `Figuras~\ref{fig:bie_fun} y~\ref{fig:rociador_fun}` se convierte en una referencia plural con `\cref{fig:bie_fun,fig:rociador_fun}` o equivalente.
- [ ] Las referencias a `fig:def_plantas`, `fig:perfil_plantas` y `fig:inicio_tramos` usan `\cref{}`.
- [ ] La redaccion no queda con duplicaciones como "la Figura \cref{...}".
- [ ] Todas las etiquetas de figuras referenciadas existen en el documento.

---

## Fase 7: Normalizacion de referencias a ecuaciones y elementos tecnicos

**Historias cubiertas**: como lector, necesito que las ecuaciones citadas en resultados y metodologia puedan localizarse sin depender de su posicion visual; como autor, quiero mantener un unico estilo de referencias cruzadas.

### Que construir

Revisar si las ecuaciones etiquetadas se mencionan en la prosa y, cuando sea util, convertir esas menciones en `\cref{}`. Esto aplica a las etiquetas `eq:hazen_williams`, `eq:perdidas_totales`, `eq:velocidad`, `eq:caudal_descarga`, `eq:factor_k_rociador` y `eq:volumen_aljibe`.

### Criterios de aceptacion

- [ ] Las ecuaciones que se usan como base de calculo estan referenciadas desde el texto cercano.
- [ ] Las referencias a ecuaciones usan `\cref{eq:...}` o `\Cref{eq:...}`.
- [ ] No se fuerzan referencias innecesarias cuando la ecuacion ya esta introducida inmediatamente antes.
- [ ] La compilacion no emite advertencias de referencias indefinidas.

---

## Fase 8: Referencias inteligentes a anejos y fichas tecnicas

**Historias cubiertas**: como lector, necesito llegar desde la memoria a las fichas tecnicas, calculos y planos anexos; como revisor, necesito que la numeracion de anejos no este escrita a mano.

### Que construir

Etiquetar el anejo de caracteristicas tecnicas y sustituir menciones manuales como "Anexo 1 (Caracteristicas tecnicas)", "los anexos" o rutas de PDF en texto por referencias inteligentes. Mantener las rutas de PDF solo cuando aporten valor operativo, no como sustituto de una referencia cruzada.

### Criterios de aceptacion

- [ ] El anejo `Caracteristicas tecnicas` tiene una etiqueta estable, por ejemplo `\label{anex:caracteristicas}`.
- [ ] Las fichas de BIE y rociador se remiten a `\cref{anex:caracteristicas}` desde la seccion de seleccion de equipos.
- [ ] Los calculos complementarios se remiten a `\cref{anex:calculos}`.
- [ ] Los planos ejecutivos se remiten a `\cref{anex:planos}`.
- [ ] No queda texto que dependa de una numeracion manual como "Anexo 1" si puede resolverse mediante `cleveref`.

---

## Fase 9: Ajuste fino de configuracion `cleveref`

**Historias cubiertas**: como autor, necesito que la salida en castellano sea correcta; como lector, necesito etiquetas coherentes para singular, plural e inicio de frase.

### Que construir

Verificar si la configuracion actual de `cleveref` cubre correctamente figuras, tablas, ecuaciones y el contador personalizado de anejos. Anadir `\Crefname` para anejos si al compilar se detecta que el inicio de frase no usa "Anexo/Anexos" correctamente.

### Criterios de aceptacion

- [ ] `\cref{fig:...}` imprime "Figura" o "Figuras" segun corresponda.
- [ ] `\cref{anex:...}` imprime "Anexo" o "Anexos" con enlaces correctos.
- [ ] `\Cref{...}` funciona correctamente al inicio de frase.
- [ ] No se rompen enlaces de `hyperref`.
- [ ] No se introducen redefiniciones innecesarias si `babel` y `cleveref` ya resuelven el caso.

---

## Fase 10: Compilacion y verificacion final

**Historias cubiertas**: como autor, necesito confirmar que la memoria compila; como revisor, necesito evidencias de que no quedan citas, referencias ni enlaces rotos.

### Que construir

Compilar el proyecto LaTeX con el ciclo completo de bibliografia y revisar el log. Corregir referencias indefinidas, citas no resueltas, entradas duplicadas de indice o problemas de nombres en castellano.

### Criterios de aceptacion

- [ ] La compilacion final genera PDF correctamente.
- [ ] `biber` se ejecuta sin errores.
- [ ] No quedan advertencias de `Citation ... undefined`.
- [ ] No quedan advertencias de `Reference ... undefined`.
- [ ] La bibliografia se imprime con las fuentes citadas.
- [ ] Las referencias a figuras, ecuaciones y anejos son clicables y muestran texto coherente.

---

## Desglose propuesto para validacion

1. **Auditoria de anotaciones**: cubre la revision de enlaces web y fuentes ya usadas en `Proyecto/Anotaciones/`.
2. **Consulta de NotebookLM**: cubre la conexion con `PCI_Practica` mediante `nlm-skill` y la recopilacion de normativa empleada.
3. **Inventario bibliografico PCI**: cubre la necesidad de sustituir referencias heredadas y crear claves bibliograficas reales.
4. **Activacion de bibliografia**: cubre la conexion `main.tex` - `refs.bib` y la impresion antes de anejos.
5. **Citas en bloques tecnicos**: cubre trazabilidad normativa, fichas de fabricante y criterios de calculo.
6. **Figuras con `cleveref`**: cubre referencias cruzadas a imagenes del cuerpo principal.
7. **Ecuaciones con `cleveref`**: cubre referencias a formulacion hidraulica y calculos.
8. **Anejos con `cleveref`**: cubre fichas tecnicas, calculos y planos.
9. **Ajustes de nombres**: cubre castellano, singular/plural y mayusculas de `cleveref`.
10. **Compilacion final**: cubre verificacion con `biber` y ausencia de referencias rotas.

La granularidad esta pensada para poder ejecutar y verificar cada fase sin mezclar bibliografia, redaccion y compilacion en una sola intervencion.

---

## Riesgos y controles

- **Riesgo**: `refs.bib` contiene material de otro proyecto.  
  **Control**: auditar claves usadas y eliminar o aislar entradas no relacionadas antes de citar.

- **Riesgo**: enlaces web de anotaciones acaban impresos como bibliografia normativa.  
  **Control**: usar esos enlaces solo para identificacion y trazabilidad; registrar normas y reglamentos sin `url` ni `urldate`.

- **Riesgo**: el notebook `PCI_Practica` no esta accesible por sesion expirada.  
  **Control**: ejecutar `nlm login --check` y repetir `nlm login` si aparece error de autenticacion.

- **Riesgo**: NotebookLM devuelve fuentes de apoyo no usadas realmente en la memoria.  
  **Control**: cruzar la lista con `main.tex`, `Proyecto/Anotaciones/` y `Normativa/` antes de crear claves bibliograficas.

- **Riesgo**: bibliografia duplicada en el indice.  
  **Control**: comprobar si `biblatex` ya anade entrada al TOC antes de usar `\addcontentsline`.

- **Riesgo**: `\cref{}` sobre el contador personalizado de anejos no imprime el texto esperado.  
  **Control**: compilar una vez tras etiquetar anejos y ajustar `\crefname` / `\Crefname` solo si es necesario.

- **Riesgo**: convertir referencias manuales deja frases redundantes.  
  **Control**: revisar cada frase completa, no hacer solo sustitucion mecanica.

- **Riesgo**: citas normativas excesivas vuelven ilegible la prosa.  
  **Control**: citar por bloques de contenido y no repetir la misma fuente en cada oracion consecutiva.

## Plan de verificacion

- Ejecutar una busqueda de enlaces en `Proyecto/Anotaciones/` y confirmar que cada fuente relevante queda clasificada.
- Verificar que se ha consultado `PCI_Practica` mediante `nlm-skill` y que la normativa recopilada queda reflejada en el inventario.
- Revisar `refs.bib` para confirmar que las entradas normativas no contienen `url`, `urldate` ni notas de fecha de acceso.
- Ejecutar una busqueda de control para confirmar que no quedan patrones `Figura~\ref`, `Figuras~\ref`, `Anexo 1` ni `\ref{fig:` en el cuerpo principal.
- Ejecutar una busqueda de claves `\cite`, `\parencite`, `\textcite` o equivalentes y cruzarlas con `refs.bib`.
- Compilar con ciclo completo de bibliografia.
- Revisar el PDF generado: indice, bibliografia, enlaces a figuras, enlaces a ecuaciones y enlaces a anejos.
- Confirmar que las fuentes bibliograficas impresas son pertinentes para proteccion contra incendios.

## Supuestos

- La revision se aplicara sobre `Practica_PCI_LaTeX/main.tex` y `Practica_PCI_LaTeX/refs.bib`.
- La carpeta `Proyecto/Anotaciones/` actua como fuente de trazabilidad para enlaces y decisiones previas, pero no todas sus URLs deben convertirse en entradas bibliograficas.
- El notebook `PCI_Practica` existe o puede localizarse por nombre/alias con `nlm`.
- No se modificara el contenido tecnico de calculos salvo cuando sea necesario para insertar citas o referencias cruzadas.
- La fuente documental de las fichas tecnicas corresponde a los PDFs ya incorporados como anejos.
- El termino operativo en la memoria sera "Anexo" en la salida de referencias cruzadas, aunque la peticion mencione "anejos".
