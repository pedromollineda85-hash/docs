# Revisión del Portal Clínico Unificado: de la v8 a la v9

**Fecha:** 3 de octubre de 2026
**Archivos:** `portal_unificado_v9.html` (nueva versión) · `portal_unificado_v8_original.html` (respaldo intacto)

---

## 1. Resumen

| | v8 | v9 |
|---|---|---|
| Campos de formulario (14 portales) | 3.671 | 3.586 (3.570 conservados + 16 nuevos de reflejos) |
| Datos que se pedían dos o más veces | 63 campos o bloques | 0 en la lista revisada |
| EVA (escala de dolor) guardada al pulsar 💾 | ❌ No se guardaba | ✅ Sí |
| Tinetti (marcha) guardado | ❌ No se guardaba | ✅ Sí |
| Mapas corporales (cuerpo, columna, vísceras, cráneo) guardados | ❌ No se guardaban | ✅ Sí |
| Historias por especialidad visibles en el panel de pacientes | ❌ No | ✅ Sí |
| Historias guardadas con la v8 se abren en la v9 | — | ✅ 3.504/3.504 campos verificados |

> ⚠️ **Hallazgo importante.** En la v8, las escalas EVA de colores, los radios de Tinetti y todos los mapas corporales **se perdían al guardar o exportar**. Solo se guardaban los campos de texto, las listas y las casillas. Las historias antiguas no traen esos datos, porque nunca se guardaron. A partir de la v9 sí se conservan.

---

## 2. Datos repetidos eliminados

Criterio: cada dato se pregunta **una sola vez**, en la sección donde tiene más sentido clínico. Si dos campos medían lo mismo, se conservó el más objetivo o el que tenía más contexto.

### En todos los portales (14)
- **Firma terapeuta.** Repetía el campo *Terapeuta* de la sección 01. Al imprimir aparece una línea de firma con el nombre del terapeuta.
- **Edad.** Ahora se calcula sola desde la fecha de nacimiento (antes se escribían las dos).
- **«NPRS dolor actual (0-10)»** en Escalas funcionales: repetía la EVA actual de la sección de dolor. Se eliminó en Cervical, Cadera, Codo, Muñeca, Mano, Pie y Dorsal.

### 🦴 Osteopatía (el caso que señalaste)
| Eliminado | Por qué |
|---|---|
| EVA PRE-tratamiento (sección 10) | Es la misma EVA «Intensidad actual» de la sección 02. Ahora la 02 sirve como EVA pre y el Δ pre→post se calcula solo. |
| Movilidad hepática, gástrica, colon descendente, cecoapéndice y vejiga (07) | Repetían los cuadrantes HD, EPI, FII, FID e HIP del mapa visceral de 9 cuadrantes. El mapa ya se guarda y su leyenda es Tensión / Doloroso / Defensa. |
| «Síntomas viscerales referidos» (6 casillas, 07) | Repetían la revisión por sistemas de la sección 03 (digestivo, génito-urinario, cardiorrespiratorio, neurológico). |
| Traumatismos relevantes (03) | Ya está en «Músculo-esqueléticos: fracturas, esguinces…». |
| Columna vertebral marcada dos veces (anterior + posterior) | Ahora hay un solo punto por vértebra. El mapa indica el **nivel exacto** y la tabla TART caracteriza la **región**. |

### Resto de portales
| Portal | Eliminado / corregido |
|---|---|
| **Lumbar** | Bloque EVA actual/mín/máx fuera de sección, duplicado de EVA reposo/movimiento/nocturno · barra EVA vacía · «Hormigueo» (= parestesias) · «Espasmo muscular» (= contractura paravertebral D/I) · **Sección 09 Dermatomas** (duplicaba la 08 y sus tablas nunca se llenaban) · Reflejos ROT y cutáneos de la sección 07: **estaban vacíos**; ahora tienen campos reales · Schober: el incremento se calcula solo |
| **Hombro** | Bloque EVA duplicado · «Atrofia muscular visible» en síntomas (ya está en Inspección) · «Escala de dolor nocturno» (= EVA nocturno) |
| **Rodilla** | Bloque EVA duplicado · «Derrame articular» en síntomas (ya están Edema, palpación de derrame, test del charco y ballottement) · «Dolor en escaleras» (= EVA escaleras) · Se añadió **Reflejo aquíleo I**, que faltaba · Etiqueta «Alineamiento rodilla **D**» |
| **Running** | Tinetti y la batería de equilibrio geriátrica: no sirven en deportistas (efecto techo) y ya están SLS, hop tests y Romberg en la sección 06 |
| **Cadera** | Fila SLR/Lasègue en Tests (ya está D/I en Neurológico) · etiqueta corregida: la escala 17-68 es **TSK-17 (Tampa)**, no FABQ |
| **Codo** | «Ángulo de carga» (= *carrying angle* medido en grados en la goniometría) · «Pivot-shift posterolateral» (= fila de Tests) · etiqueta TSK-17 corregida |
| **Muñeca** | «Allen test» (= fila de Tests) · «Atrofia tenar visible» (= Eminencia tenar en Inspección) |
| **Mano** | «Mano predominante en actividades» (= Dominancia) · «Allen digital» (= fila de Tests) · «Kapandji» (= fila de la goniometría del pulgar) |
| **Pie** | «Test Jack (windlass)» (= fila de Tests) · «Tinel posterior tibial» (= fila de Tests) · fila «Single leg heel raise» (se conserva el campo con nº de repeticiones) |
| **Dorsal** | 5 filas de Tests que repetían campos: Adams, Schober torácico, reflejos abdominales, Babinski + Hoffmann, BASDAI · «Cobb» en Escalas (= Cobb en Inspección) · SRS-22r con rango correcto (media 1-5) |
| **Medular** | «WISCI II» estaba en las secciones 06 y 07; se conserva en Escalas · casilla «Disfunción respiratoria» (= Función respiratoria detallada en la 03) |

---

## 3. Mejoras de rapidez (criterio: capturar más en menos tiempo)

1. **Datos del paciente compartidos.** Si pasas de un portal a otro con el mismo paciente (p. ej. Osteopatía → Lumbar), se copian solos nombre, fecha de nacimiento, edad, sexo, profesión, dominancia, terapeuta y médico. Un aviso permite vaciarlos si es otro paciente. Solo dura la sesión; al recargar se borra, por seguridad.
2. **Fecha de evaluación de hoy** por defecto.
3. **Botón «⚡ Normal en vacíos»** en las tablas de tests, la neurológica, la muscular y la TART. Marca como Negativo / Normal / 5 / No **solo las casillas vacías**. Primero marcas los hallazgos positivos y luego completas el resto con un clic.
4. **Autoguardado de borrador** cada pocos segundos. Si se cierra el navegador sin guardar, al volver al portal te ofrece **Recuperar**.
5. **Nombre del paciente propuesto** al pulsar 💾 Guardar.
6. **Panel de pacientes** con la lista «Historias por especialidad» (buscable) y botón **Abrir**.

---

## 4. Valoración del portal (criterios digitales y clínicos)

Escala: ★ débil · ★★★ correcto · ★★★★★ excelente

| Criterio | Nota | Comentario |
|---|---|---|
| Cobertura clínica por región | ★★★★★ | 14 portales con anamnesis, banderas rojas, ROM AAOS, tests con estructura evaluada, neurológico, Daniels/MRC y escalas validadas. Más completo que la mayoría de plantillas comerciales. |
| Seguridad clínica (banderas rojas) | ★★★★☆ | Muy completo (reglas de Ottawa, cauda equina, VBI, TVP…). Falta un aviso visual automático cuando se marca alguna. |
| Base de evidencia | ★★★★☆ | Usa escalas validadas (ODI, NDI, KOOS, HOOS, DASH, PRWE, VISA, ASIA/ISNCSCI, NIHSS, Fugl-Meyer, Berg…). Algunos tests muestran sensibilidad y especificidad. En Osteopatía faltan PROMs propios (ver §6). |
| Rapidez de captura | ★★★☆☆ → ★★★★☆ | En la v8, con 200-300 campos por portal y datos repetidos, era lento. La v9 elimina repeticiones y añade copia de datos, «Normal en vacíos» y autoguardado. |
| Integridad de los datos | ★★☆☆☆ → ★★★★☆ | La v8 perdía EVA, Tinetti y mapas al guardar, y su formato (por posición) se rompía al cambiar el formulario. La v9 usa claves estables y es compatible con la v8. |
| Explotación de datos / investigación | ★★☆☆☆ | Los datos quedan en el navegador (localStorage), sin base común ni exportación tabular (CSV). Es el mayor límite para el respaldo científico (ver §6). |
| Seguridad / RGPD | ★★☆☆☆ | Sin usuario/contraseña ni cifrado. Los datos viven en un solo navegador y se pierden si se borra el historial. Haz copias con **Exportar JSON**. |
| Usabilidad en tablet | ★★★☆☆ | Funciona, pero las tablas anchas exigen desplazamiento horizontal en pantallas pequeñas. |

---

## 5. Comparación con sistemas del mercado

| Función | **Tu portal v9** | Cliniko / Jane / TM3 (gestión clínica general) | WebPT (EMR de fisioterapia, EE. UU.) | iFisia / OsteoDiagnostic, Fisiosalus (España) | Pabau / eMedicalPractice / Preve (osteopatía) |
|---|---|---|---|---|---|
| Plantillas específicas por región (14) | ✅ Muy detalladas | Plantillas genéricas que crea el usuario | ✅ ROM, MMT y PROMs estructurados | ✅ Plantillas de fisio y osteo | ✅ Plantillas y diagramas corporales |
| TART + mapa visceral + craneosacral + cadenas GDS/RPG | ✅ (muy poco habitual) | ❌ | ❌ | Parcial | Diagramas de columna y extremidades |
| Escalas validadas con interpretación | ✅ Muchas | Formularios a medida | ✅ | Algunas | Seguimiento de *outcomes* |
| PROMs que rellena el paciente (en casa o en el móvil) | ❌ | ✅ (formularios online) | ✅ | Parcial | ✅ (Preve) |
| Agenda, facturación, consentimiento informado | ❌ | ✅ | ✅ | ✅ | ✅ |
| Datos en la nube, multiusuario, copias de seguridad | ❌ (navegador local) | ✅ | ✅ | ✅ | ✅ |
| Gráficas de evolución (EVA, escalas por sesión) | ❌ | Parcial | ✅ | Parcial | ✅ |
| Coste | Gratuito, sin conexión | Suscripción mensual | Suscripción | Suscripción | Suscripción |

**Conclusión.** Clínicamente, tu portal es **más profundo** que el software comercial, sobre todo en osteopatía (TART, visceral, craneosacral, cadenas), donde casi ningún producto llega a este detalle. Donde pierde es en **infraestructura**: PROMs online, nube, multiusuario, evolución gráfica y exportación para investigación.

---

## 6. Recomendaciones priorizadas (siguientes pasos)

1. **Exportar a CSV o Excel** todas las historias de un portal. Es imprescindible para el respaldo científico: estadística, series de casos y publicaciones. *Esfuerzo bajo.*
2. **PROM osteopático estándar.** Añadir el **Bournemouth Questionnaire modificado** (lo usa el NCOR del Reino Unido en sus PROMs nacionales de osteopatía) o el **MSK-HQ** (14 ítems, válido para cualquier región) en la primera visita y en el alta. Así los resultados son comparables con la literatura. *Esfuerzo bajo.*
3. **Evolución por sesión** en cada portal: fecha, EVA, escala principal, técnicas aplicadas y respuesta, con un mini-gráfico. Hoy la evolución solo existe en la HC antigua del panel. *Esfuerzo medio.*
4. **Aviso automático de banderas rojas** (banner rojo fijo y en la impresión) cuando se marca alguna. *Esfuerzo bajo.*
5. **Reducir escalas redundantes** (para decidir con el equipo):
   - DASH + QuickDASH (Muñeca, Mano) → quedarse con QuickDASH.
   - KOOS + WOMAC (Rodilla) y HOOS + WOMAC (Cadera) → WOMAC se puede derivar de KOOS y HOOS.
   - FAAM + FADI (Pie) → FAAM.
   - SF-36 + WHOQOL-BREF (Medular, Neuro) → elegir una.
   - En Muñeca, «PRTEE-W» no es una escala reconocida → usar PRWE.
6. **Retirar la HC antigua de 7 pestañas** del panel (Datos / Antecedentes / Dolor…). Repite todo lo de los portales y además tiene EVA y NRS duplicadas. Hoy solo se usa para editar pacientes antiguos. *Esfuerzo medio.*
7. **Protección de datos.** Para uso real con pacientes conviene un almacenamiento con contraseña y copia de seguridad, o pasar a un sistema en la nube conforme al RGPD. Mientras tanto, **exporta JSON periódicamente**.

---

## 7. Compatibilidad y verificación

- Cada campo conserva su **clave de la v8**, así que las historias guardadas o exportadas con la v8 se abren en la v9 sin desplazamientos. Verificado en navegador: **3.504 de 3.504 campos** cargan con su valor correcto en los 14 portales.
- Prueba de ida y vuelta en la v9 (guardar → limpiar → cargar) en los 14 portales, con campos, EVA, Tinetti y mapas: **todo idéntico**.
- Sin errores de JavaScript en la v8 ni en la v9.
- Los datos de los campos eliminados que existan en historias antiguas no se borran del archivo guardado. Simplemente no se muestran.

### Fuentes de la comparación
- [Patient reported outcomes in a large cohort of patients receiving osteopathic care in the UK (PMC)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8051759/)
- [Institute of Osteopathy, recursos sobre PROMs](https://cpd.osteopathy.org.uk/resources/patient-reported-outcome-measures/)
- [NCOR, National Council for Osteopathic Research](https://www.hsu.ac.uk/national-council-for-osteopathic-research-ncor/)
- [Physitrack, documentación de fisioterapia con PROMs (WebPT, MedBridge, Raintree)](https://www.physitrack.com/es/insights/best-pt-documentation-software-outcome-measures-proms)
- [Pabau, software para osteopatía](https://pabau.com/industry/osteopathy-practice-software/)
- [eMedicalPractice, EHR para manipulación osteopática](https://emedpractice.com/?p=17284)
- [Noterro, mejores programas de gestión para osteopatía 2026](https://www.noterro.com/blog/best-osteopathy-practice-management-software)
- [Comparativa Cliniko vs Jane vs TM3 (GetApp / Software Advice)](https://www.getapp.com.au/compare/130239/1048279/cliniko/vs/tm3)
- [Software para fisioterapeutas en España (iFisia, Fisiosalus, iBeeClinic)](https://www.softwaredoit.es/software-medico/software-clinica-fisioterapia.html)
