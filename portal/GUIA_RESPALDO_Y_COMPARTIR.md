# Guía v9.1: Excel, Bournemouth, respaldo en la nube y compartir historias

## 1. Exportar a Excel

| Dónde | Botón | Qué descarga |
|---|---|---|
| Barra inferior de cada portal | **📊 Excel** | Todas las historias guardadas de ese portal: **una fila por paciente** y una columna por campo, más EVA, total de Tinetti, totales del BQ y marcas de los mapas. |
| Panel de pacientes | **📊 Exportar todo a Excel** | Todas las historias de los 14 portales en **formato largo**: una fila por dato (Paciente · Fecha · Especialidad · Campo · Valor). Es el formato ideal para tablas dinámicas, SPSS, R o Jamovi. |

- Son archivos `.csv` con separador `;` y codificación UTF-8, y se abren con doble clic en Excel en español.
- Solo se exportan las historias **guardadas con 💾**. Lo que está escrito pero sin guardar no entra.
- **Para investigación,** antes de compartir el Excel con terceros sustituye el nombre del paciente por un código. Así los datos quedan anonimizados (seudonimizados).

## 2. Cuestionario Bournemouth (BQ) en Osteopatía

- Es la **nueva sección 2b** del portal de Osteopatía: 7 ítems de 0 a 10 (dolor, actividades diarias, vida social, ansiedad, depresión, trabajo y autocontrol). El total va de 0 a 70; más alto es peor.
- **Basal** en la primera visita y **Reevaluación** en el control o el alta. El portal calcula el total, la diferencia y el % de mejora. Una mejora de **30 % o más** se marca como clínicamente relevante.
- Es la versión modificada, válida para cualquier región, que usa el NCOR (el consejo de investigación osteopática del Reino Unido) en su recogida de resultados. Los ítems están traducidos al español para uso clínico. Si vas a publicar, cita la **versión española validada** de la región correspondiente y comprueba que la redacción coincide.

## 3. Respaldo en la nube

Ahora mismo los datos viven **solo en el navegador** de tu ordenador. Si se borra el historial o se cambia de PC, se pierden. Hay dos niveles de protección.

### Nivel 1: copia manual (cualquier navegador)
1. En el panel de pacientes, pulsa **💾 Copia de seguridad**.
2. Escribe una **contraseña**, que cifra la copia con AES-256. Guárdala bien: sin ella la copia no se puede abrir.
3. Guarda el archivo descargado dentro de tu carpeta de **Google Drive**, **OneDrive** o **Dropbox**.
4. Para recuperar los datos en otro PC: **♻ Restaurar copia** y la misma contraseña.

El panel muestra la fecha de la última copia y un **aviso amarillo** si han pasado más de 7 días.

### Nivel 2: copia automática en la nube (Chrome o Edge en el ordenador)
1. Instala **Google Drive para ordenador** (o usa OneDrive, que ya viene en Windows). Crea una carpeta, por ejemplo `Mi unidad/Respaldo Portal Clínico`.
2. En el panel, pulsa **📁 Carpeta de respaldo** y elige esa carpeta.
3. Al empezar la jornada, haz **una** copia manual con contraseña (💾 Copia de seguridad).
4. Desde ese momento, **cada vez que guardes una historia** el portal actualiza solo el archivo `respaldo_portal_clinico_AUTO_cifrado.json` en esa carpeta. Drive u OneDrive lo suben a la nube y guardan versiones anteriores.

> Pide la contraseña una vez por sesión a propósito, para no guardar contraseñas en el navegador. Si no se ha hecho la copia del día, el guardado automático no se activa.

## 4. Compartir una historia con otro profesional

### Opción A: historia cifrada y editable (recomendada)
1. Con la historia abierta, pulsa **🔒 Compartir** en la barra inferior del portal.
2. Elige una contraseña de al menos 8 caracteres. Se descarga `historia_<portal>_<fecha>_cifrada.json`. El **nombre del paciente no aparece** ni en el nombre del archivo ni dentro sin la contraseña.
3. Envía el archivo por correo, WhatsApp o Drive, y **la contraseña por otro canal** (llamada o SMS).
4. El otro profesional abre su `portal_unificado_v9.html`, entra en el mismo portal, pulsa **⬆ JSON**, elige el archivo y escribe la contraseña. Recibe la historia completa y editable: campos, EVA, BQ, Tinetti y mapas. Después pulsa 💾 Guardar en su equipo.

### Opción B: informe de solo lectura
Pulsa **🖨 Imprimir** y elige **Guardar como PDF**. Sirve para enviar a médicos o mutuas, o para adjuntar a una derivación.

### Opción C: equipo que trabaja siempre junto
Comparte con los compañeros una **carpeta de Google Drive** donde dejéis las copias cifradas o las historias de cada paciente. Cada profesional las importa en su portal.

## 5. Siguiente paso posible: una historia compartida en tiempo real

Las opciones anteriores funcionan **sin servidor**: cero coste, y los datos solo salen del PC cifrados. Si queréis **varios profesionales trabajando a la vez sobre la misma historia**, hace falta:

| Elemento | Opción típica |
|---|---|
| Base de datos y usuarios | Supabase o Firebase con **servidores en la UE**, o en tu país |
| Inicio de sesión y roles | Cada profesional con su usuario; permisos por paciente |
| Registro de accesos (auditoría) | Obligatorio para datos de salud |
| Legal | Contrato de encargado del tratamiento con el proveedor, consentimiento del paciente, cumplimiento de la normativa de protección de datos y de historia clínica de tu país (en España: RGPD, LOPDGDD y Ley 41/2002) |
| Esfuerzo | Medio-alto: alojamiento web, mantenimiento y coste mensual pequeño |

Recomendación: usa unas semanas el **respaldo automático en Drive y el compartir cifrado**. Si se quedan cortos, se diseña la versión en la nube multiusuario.
