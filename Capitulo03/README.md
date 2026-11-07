# Práctica 3. Creación de un agente para investigación financiera con documentos de Microsoft 365

## Objetivo de la práctica:

Al finalizar la práctica, serás capaz de:

- Crear un agente de análisis documental en **Agent Builder de Microsoft 365 Copilot**, sin utilizar Copilot Studio.
- Incorporar documentos financieros ficticios de SharePoint y configurar instrucciones que diferencien hechos, cálculos, hipótesis y datos no documentados.
- Contrastar un análisis de emisión de bonos con sus fuentes y comparar el agente reutilizable con un prompt puntual de Copilot Chat.

## Duración aproximada:

- **35 minutos.**

## Tabla de ayuda:

| Parámetro | Valor | Uso |
|---|---|---|
| Empresa ficticia | Transportes Logísticos del Norte S.A. (**TLN**) | Emisor del caso académico. |
| Fuente **F1** | [03_Terminos_indicativos_emision_TLN.docx](recursos/03_Terminos_indicativos_emision_TLN.docx) | Condiciones propuestas y cálculo ilustrativo de cupón. |
| Fuente **F2** | [04_Nota_crediticia_TLN.docx](recursos/04_Nota_crediticia_TLN.docx) | Estados resumidos, deuda, EBITDA, riesgos y límites. |
| Fuente **F3** | [07_Minuta_revision_preliminar_TLN.docx](recursos/07_Minuta_revision_preliminar_TLN.docx) | Pendientes de diligencia; **no** equivale a aprobación. |
| Herramienta | [Microsoft 365 Copilot](https://m365.cloud.microsoft/chat) → **Nuevo agente** | Crear, configurar y probar el agente. |
| Nombre | `Asistente de Emision TLN` | Agente usado también en la práctica 4. |
| Ubicación | Carpeta `TLN_Emision` en SharePoint del laboratorio | Contener **solo F1, F2 y F3**. |
| Requisitos | [SETUP_GUIDE.md](../SETUP_GUIDE.md) | Cuenta con licencia Microsoft 365 Copilot, acceso a Agent Builder y lectura de archivos. |

> **Alcance:** Los tres archivos son fuentes **simuladas y complementarias**. F1 define la propuesta, F2 analiza los indicadores y F3 documenta solicitudes pendientes. No existe un documento de aprobación. Agregar archivos como **Conocimiento** no permite al agente ejecutar acciones en servicios externos. La práctica utiliza la licencia de Microsoft 365 Copilot disponible en el entorno.

## Instrucciones

### Tarea 1. Preparar las tres fuentes documentales (6 minutos)

**Paso 1.** Descargar **F1**, **F2** y **F3** desde la Tabla de ayuda y abrirlos brevemente. Identificar su código de fuente en el encabezado y distinguir qué función cumple cada uno.

**Paso 2.** Abrir el **sitio real de SharePoint habilitado para el laboratorio**, localizar la biblioteca de documentos y entrar en la carpeta `TLN_Emision`. Si el instructor ya cargó los tres documentos, no crear carpetas ni copias duplicadas.

**Paso 3.** Cargar los tres archivos en `TLN_Emision` mediante **Cargar > Archivos** únicamente si dispone de permisos de edición. Si la carpeta es de solo lectura, utilizar los archivos ya preparados por el administrador.

**Paso 4.** Abrir F1, F2 y F3 **desde SharePoint**, con la misma cuenta que utilizará Microsoft 365 Copilot; comprobar que el contenido es visible y que no se está usando una ruta local o un vínculo de uso compartido caducado.

**Paso 5.** Comprobar la coherencia mínima del expediente: monto propuesto **12 millones USD** en F1; deuda financiera **18,5 millones USD**, efectivo **2 millones USD** y EBITDA **10,122 millones USD** en F2; y **ausencia de aprobación** en F3. Los tres documentos no representan información auditada.

### Tarea 2. Crear el agente y definir sus reglas de investigación (13 minutos)

**Paso 1.** Acceder a [Microsoft 365 Copilot](https://m365.cloud.microsoft/chat), abrir **Nuevo agente / New agent** y seleccionar **Omitir para configurar / Skip to configure**, o la opción equivalente de **Configurar** de Agent Builder. No abrir el portal de Copilot Studio.

**Paso 2.** Introducir los parámetros siguientes:

| Campo | Valor |
|---|---|
| Nombre | `Asistente de Emision TLN` |
| Descripción | Agente para el análisis preliminar de una emisión ficticia de bonos de TLN, sustentado en tres documentos internos simulados de Microsoft 365. |
| Fuentes de conocimiento | F1, F2 y F3 de `TLN_Emision` |
| Destino | Uso dentro de Microsoft 365 Copilot; sin acciones ni publicación externa. |

**Paso 3.** Abrir **Instrucciones / Instructions** y pegar el siguiente texto íntegro. Conservar las referencias **F1**, **F2** y **F3** para comprobar la procedencia de la respuesta.

**Instrucciones del agente — Emisión TLN**

```text
Eres un analista documental para el expediente académico, ficticio y no
vinculante de Transportes Logísticos del Norte S.A. (TLN).

Fuentes autorizadas:
- F1: términos indicativos de una emisión de bonos.
- F2: nota crediticia preliminar con cifras simuladas y riesgos.
- F3: minuta de revisión preliminar con verificaciones pendientes.

Reglas:
1. Basa las respuestas sobre TLN únicamente en F1, F2 y F3. Identifica
   el código y el nombre de los documentos utilizados. Prioriza una cita
   o referencia verificable a la fuente cuando la interfaz lo permita.
2. Distingue siempre: HECHO DOCUMENTADO, CÁLCULO, HIPÓTESIS y DATO FALTANTE.
3. Nunca conviertas una propuesta en emisión colocada, una solicitud de
   documentación en información recibida ni una revisión en aprobación.
4. Muestra operaciones matemáticas, unidad, fecha de corte y supuestos.
5. No inventes calificaciones externas, autorizaciones, garantías,
   covenants, cronogramas contractuales, flujo de caja ni datos de mercado.
6. No atribuyas a TLN el contenido de páginas públicas ajenas al caso.
   Si después se agrega un conector web, separa el CONTEXTO EXTERNO de
   los hechos internos de TLN.
7. Si faltan pruebas para valorar una emisión o estimar capacidad real de
   pago, responde "No documentado" e indica los soportes necesarios.
8. No emitas recomendaciones de inversión, no modifiques documentos y no
   ejecutes operaciones financieras.
9. Responde en español con una tabla breve cuando haya indicadores y con
   una lista de preguntas pendientes cuando se trate de diligencia.
```

**Paso 4.** Ir a **Configurar > Conocimiento / Knowledge**, seleccionar **Examinar / Browse** (archivos en la nube) y buscar la carpeta `TLN_Emision`. Elegir los archivos **F1, F2 y F3**, no toda la biblioteca ni el sitio raíz.

**Paso 5.** Verificar que **los tres nombres de archivo aparecen** en la lista de conocimiento del agente. Si alguna fuente muestra **Preparando / Preparing**, comprobar su estado antes de evaluar las respuestas. Si no se puede seleccionar el documento, verificar permisos y ubicación, sin reemplazarlo por un documento de otro caso.

**Paso 6.** Guardar o crear el agente y entrar en **Probar / Try it**. Confirmar que se puede conversar con el agente; no compartirlo públicamente ni agregar herramientas de Power Platform.

### Tarea 3. Investigar la operación y comprobar la trazabilidad (10 minutos)

**Paso 1.** Enviar la primera consulta al agente.

**Prompt 1 — Ficha de la propuesta**

```text
Prepara una ficha de la emisión propuesta de TLN: monto, moneda, fecha
indicativa de colocación, plazo, cupón, periodicidad y aplicación tentativa
de recursos. Separa términos propuestos de decisiones aprobadas. Incluye
una referencia a F1 para cada grupo de datos y aclara qué falta definir.
```

**Paso 2.** Contrastar con **F1**: **12 000 000 USD**, fecha propuesta **01/12/2026**, plazo **36 meses**, cupón nominal anual fijo **8,25 %**, pago previsto **semestral** y reparto ilustrativo de fondos **7,2 millones USD a refinanciación / 4,8 millones USD a equipamiento**. Comprobar que esta distribución es tentativa y que **no existe una autorización de emisión**.

**Paso 3.** Enviar la consulta financiera:

**Prompt 2 — Indicadores y límites de endeudamiento**

```text
Usa F1 y F2 para calcular: (a) crecimiento de ingresos de 2024 a 2025,
(b) deuda financiera neta de 2025, (c) deuda neta / EBITDA 2025 y
(d) cupón semestral nominal ilustrativo sobre la emisión completa.
Presenta cada operación, unidades y fecha. Explica por qué estos cálculos
no prueban capacidad de pago ni permiten afirmar el saldo de deuda
posterior a la refinanciación propuesta.
```

**Paso 4.** Verificar **13,4 %** de crecimiento de ingresos, deuda neta **16,5 millones USD**, deuda neta/EBITDA **≈1,63x** y cupón semestral **495 000 USD** (`12 000 000 × 0,0825 / 2`). El agente debe reconocer que no hay flujo de caja libre, calendario contractual ni condiciones finales.

**Paso 5.** Enviar una consulta sobre decisiones y evidencias incompletas:

**Prompt 3 — Revisión del comité y dato no disponible**

```text
¿La emisión de TLN fue aprobada? ¿Qué calificación crediticia externa
se asignó? ¿Cuáles son las tres verificaciones documentales más urgentes
para analizar el servicio de deuda? Utiliza la minuta F3, contrasta con
F1 y F2 e identifica explícitamente lo que no está documentado.
```

**Paso 6.** Comprobar con **F3** que solo hubo una **reunión exploratoria**, sin votación ni aprobación; no existe calificación externa documentada; y siguen pendientes, entre otros, **flujo de caja (DD-02)**, **detalle de deuda (DD-03)** y **estructura y calendario contractual (DD-07)**. Corregir las instrucciones si el agente confunde solicitudes con información ya entregada.

### Tarea 4. Contrastar el agente con un prompt puntual de Copilot Chat (6 minutos)

**Paso 1.** Abrir una **conversación nueva de Copilot Chat** sin seleccionar el agente TLN y adjuntar **F1, F2 y F3 desde SharePoint** como referencias de la conversación.

**Paso 2.** Enviar este prompt con el mismo alcance documental:

**Prompt comparativo — Consulta puntual con las mismas fuentes**

```text
Basándote solo en F1, F2 y F3 adjuntos, resume la emisión propuesta de TLN,
calcula deuda neta/EBITDA y cupón semestral nominal, indica si existe
aprobación y enumera tres evidencias pendientes. Cita los documentos,
distingue cálculos de hechos y no inventes datos externos.
```

**Paso 3.** Comparar **contenido y trazabilidad**, no la redacción literal: los valores y límites deben coincidir. Identificar la ventaja del agente: conservar las **instrucciones y las fuentes definidas** para futuras preguntas, sin tener que repetirlas en cada conversación.

**Paso 4.** Volver al agente `Asistente de Emision TLN` y comprobar que permanece entre los agentes creados y que las tres fuentes siguen asociadas. No añadir todavía el conector web: esa integración pertenece a la práctica 4.

### Resultado esperado

Existe el agente **`Asistente de Emision TLN`**, creado en **Microsoft 365 Copilot con Agent Builder**, con **F1, F2 y F3** como conocimiento procedente de SharePoint. Su respuesta distingue una **emisión propuesta y no aprobada** de **12 millones USD**, cupón **8,25 %**, pago semestral ilustrativo **495 000 USD**, deuda neta de **16,5 millones USD**, deuda neta/EBITDA **≈1,63x** y tres diligencias pendientes. No inventa autorización, rating, garantías ni calendario definitivo. El contraste con Copilot Chat utiliza los **mismos documentos** y no implica resultados textuales idénticos.

Documentación oficial: [Crear agentes con Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents) · [Fuentes de conocimiento en Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge).

---

# Práctica 4. Integración de un conector de sitio web empresarial para investigación financiera

## Objetivo de la práctica:

Al finalizar la demostración, serás capaz de:

- Incorporar al agente existente una **conexión administrada Enterprise Websites** de Microsoft 365 Copilot que el instructor haya comprobado previamente.
- Consultar información económica o financiera **externa** recuperada de la conexión y comprobar las citas a páginas originales.
- Distinguir un conector empresarial indexado de **Búsqueda en la web** y de los documentos **F1, F2 y F3** de TLN.

## Duración aproximada:

- **5 minutos. Demostración del instructor.**

## Tabla de ayuda:

| Parámetro | Valor | Uso |
|---|---|---|
| Agente | `Asistente de Emision TLN` | Agente de la práctica 3, con F1–F3. |
| Conector | **Enterprise Websites / Sitio web empresarial** | Conexión de conocimiento de solo lectura, indexada por el administrador. |
| Nombre convenido | `FinanzasWebCurso` | Nombre **propuesto** en la [SETUP GUIDE](../SETUP_GUIDE.md); verificar el nombre real. |
| Fuente primaria candidata | [Banco Mundial](https://www.worldbank.org/) | Perspectivas económicas y desarrollo. |
| Alternativas, solo si se validan | [BID](https://www.iadb.org/), [Investopedia](https://www.investopedia.com/) | Financiamiento/desarrollo o conceptos de inversiones. |
| Ficha de elección de fuente | [05_Fuentes_web_financieras.md](recursos/05_Fuentes_web_financieras.md) | Utilizar el prompt asociado al **único sitio validado**. |
| Comprobaciones previas | [06_Validacion_conector_web.md](recursos/06_Validacion_conector_web.md) | Criterios del instructor, preparados antes de la clase. |

> **Preparación obligatoria:** Los **5 minutos no incluyen la creación ni el rastreo del conector**. El administrador debe confirmar **antes del curso** que existe una conexión con páginas indexadas y que dicha conexión se puede **seleccionar y consultar desde Agent Builder**. Son tres sitios candidatos, **no tres conexiones garantizadas**. Una conexión que aparece en el centro de administración, pero no en Agent Builder, **no satisface esta demostración**. La búsqueda web libre no es sustituto del conector.

## Instrucciones

### Tarea 1. Incorporar al agente la conexión financiera preparada (2 minutos)

**Paso 1.** Abrir en Microsoft 365 Copilot el agente `Asistente de Emision TLN` y seleccionar **Editar / Configurar > Conocimiento**. Confirmar que **F1, F2 y F3** siguen presentes.

**Paso 2.** Seleccionar **Elegir otros orígenes de datos / Choose other data sources** y buscar el conector administrado **Enterprise Websites** y la conexión previamente validada (por ejemplo, `FinanzasWebCurso`). Agregar **esa conexión**, no una URL pública mediante la opción **Sitio web**.

**Paso 3.** Comprobar que el origen agregado aparece en **Conocimiento** y guardar los cambios. Si no figura en las opciones del agente, **detener la demostración del conector**; no activar la búsqueda web para simular la integración.

### Tarea 2. Consultar la fuente financiera indexada (2 minutos)

**Paso 1.** Abrir **Probar / Try it** y enviar el **prompt del sitio validado** disponible en [05_Fuentes_web_financieras.md](recursos/05_Fuentes_web_financieras.md). Utilizar **solo el sitio que el administrador indicó como indexado**. Este es el prompt correspondiente al **Banco Mundial**, si fue el elegido:

**Prompt — Contexto externo para el análisis**

```text
Usa exclusivamente el conocimiento de la conexión empresarial
FinanzasWebCurso, que indexa páginas públicas del Banco Mundial.
Identifica dos temas de perspectivas económicas o desarrollo descritos
por páginas recuperadas del conector. Para cada tema:
1. Resume brevemente qué señala la fuente.
2. Aporta el título o URL de la página indexada.
3. Formula una pregunta que el analista de TLN debería investigar.

Separa CONTEXTO EXTERNO de DATOS INTERNOS TLN. No atribuyas cifras,
proyectos o afirmaciones del Banco Mundial a TLN; no inventes estadísticas.
Si el conector no recupera páginas, indica "Fuente externa no recuperada".
No sustituyas silenciosamente el conector por Búsqueda en la web.
```

**Paso 2.** Abrir al menos **una cita o vínculo** de la respuesta y comparar el texto citado con la página pública. La información externa ofrece **preguntas de contexto** para TLN; no demuestra los indicadores internos ni la viabilidad de la emisión.

### Tarea 3. Comprobar los límites de la integración (1 minuto)

**Paso 1.** Identificar en **Conocimiento** la diferencia entre **F1–F3 (SharePoint)** y **FinanzasWebCurso (páginas web indexadas)**. Reconocer que el conector no ejecuta acciones, modifica archivos ni entrega datos de mercado en tiempo real.

**Paso 2.** Verificar que la respuesta cita realmente la fuente empresarial seleccionada. Si no puede demostrarse qué conexión se usó, clasificar la prueba como **no validada**, aun cuando el agente haya redactado una respuesta aparentemente correcta.

### Resultado esperado

El mismo agente de la práctica 3 contiene una **conexión Enterprise Websites administrada, indexada y visible en Agent Builder**. La consulta devuelve al menos **una página del sitio elegido** cuya cita puede abrirse y comprobarse. El participante distingue **contexto económico externo** de los hechos de TLN y reconoce que la integración **es de conocimiento, no de ejecución de acciones**. Si falla cualquiera de estas verificaciones, **no se afirma que el conector está funcionando**.

Documentación oficial: [Enterprise Websites](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/enterprise-web-connector) · [Conectores como conocimiento en Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge).

---

# Práctica 5. Seguimiento financiero recurrente con revisión humana

## Objetivo de la práctica:

Al finalizar la práctica, serás capaz de:

- Crear un **prompt programado** para el seguimiento simulado de un fondo, mediante Microsoft 365 Copilot, cuando la capacidad esté habilitada.
- Contrastar la ejecución con un libro de tres indicadores y una ficha de contexto de Asset Management.
- Identificar variaciones, datos ausentes y límites de una recurrencia que **no actualiza por sí misma las fuentes**.

## Duración aproximada:

- **22 minutos.**

## Tabla de ayuda:

| Parámetro | Valor | Uso |
|---|---|---|
| Fondo ficticio | **Fondo Alfa Capital** | Seguimiento de Asset Management, no de TLN. |
| Fuente A0 | [Indicadores_Fondo_Alfa.xlsx](recursos/Indicadores_Fondo_Alfa.xlsx) | Registros del **16, 23 y 30/10/2026**. |
| Fuente A1 | [08_Contexto_y_control_Fondo_Alfa.docx](recursos/08_Contexto_y_control_Fondo_Alfa.docx) | Definiciones y criterios de revisión humana. |
| Comparación requerida | **23 frente a 30 de octubre de 2026** | Dos últimos cortes del libro. |
| Herramienta | **Copilot Chat → Programar este mensaje / Schedule this prompt** | Crear y probar una tarea recurrente. |
| Cadencia | Semanal, lunes, en el horario de laboratorio aprobado | Ejemplo de seguimiento; **no** es dato de mercado en vivo. |
| Requisitos | [SETUP_GUIDE.md](../SETUP_GUIDE.md) | Microsoft 365 Copilot habilitado, experiencias conectadas y acceso a documentos en la nube. |

> **Separación de escenarios:** El **Fondo Alfa Capital** es distinto del emisor TLN. El agente `Asistente de Emision TLN` de las prácticas 3–4 **no se reutiliza** para la programación del fondo. Esta práctica se realiza en **Copilot Chat**, no en Copilot Studio ni mediante una acción del conector web. La programación repite el prompt, pero **no actualiza el Excel ni garantiza que las referencias adjuntas se conserven** en cada ejecución.

## Instrucciones

### Tarea 1. Preparar y comprobar las fuentes del fondo (4 minutos)

**Paso 1.** Descargar **A0** y **A1** desde la Tabla de ayuda. Abrir el libro en Excel y revisar sus hojas **Fondo**, **Criterios**, **Contexto** e **Incidencias**.

**Paso 2.** Comprobar los dos últimos cortes de A0:

| Indicador | 23/10/2026 | 30/10/2026 |
|---|---:|---:|
| Patrimonio administrado | **126 400 000 USD** | **124 600 000 USD** |
| Rendimiento mensual acumulado | **0,8 %** | **0,4 %** |
| Liquidez | **9,5 %** | **Dato no disponible** |

**Paso 3.** Cargar el libro y la ficha en una carpeta autorizada de **SharePoint o OneDrive** si aún no están preparados; abrir ambos desde la nube con la misma identidad utilizada en Copilot Chat.

**Paso 4.** Confirmar que la liquidez del 30/10 es una **celda vacía intencional**, no el valor cero. Revisar en A1 la advertencia de que la variación de patrimonio **no revela por sí sola su causa**.

### Tarea 2. Obtener y verificar el reporte inicial (7 minutos)

**Paso 1.** Abrir **Copilot Chat en la experiencia de trabajo** con la licencia Microsoft 365 Copilot. Iniciar un chat nuevo y agregar **A0 y A1 como referencias a archivos de Microsoft 365**, no únicamente a copias locales.

**Paso 2.** Enviar el siguiente mensaje tal como aparece. El nombre de los archivos forma parte del criterio de comprobación de acceso.

**Prompt 1 — Reporte del fondo con validación de origen**

```text
Elabora un reporte didáctico del Fondo Alfa Capital utilizando SOLAMENTE
los archivos de Microsoft 365 indicados en esta conversación:
- Indicadores_Fondo_Alfa.xlsx (fuente primaria de los valores).
- 08_Contexto_y_control_Fondo_Alfa.docx (definiciones y límites).

Compara los cortes 23/10/2026 y 30/10/2026. Entrega:
1. Una tabla de patrimonio USD, rendimiento mensual acumulado % y liquidez %
   por fecha, indicando la fuente de cada valor.
2. Variación absoluta del patrimonio en USD y cambio del rendimiento en
   puntos porcentuales, con las dos operaciones mostradas.
3. La leyenda "Dato no disponible" en la liquidez del último corte.
4. Dos preguntas de revisión humana antes de divulgar el informe.
5. Fecha real del último corte disponible en los documentos; no presentes
   estas cifras de octubre como información financiera actual o en vivo.

No infieras flujos, causas, calificaciones ni recomendaciones de inversión.
Si NO puedes recuperar y contrastar los dos archivos, responde "No se pudo
consultar la fuente" y NO inventes los indicadores.
```

**Paso 3.** Contrastar la respuesta con **A0** y **A1**. Verificar que calcula `124 600 000 − 126 400 000 = −1 800 000 USD` y `0,4 % − 0,8 % = −0,4 puntos porcentuales`.

**Paso 4.** Comprobar que el informe **no** presenta el valor **9,5 %** de liquidez del 23/10 como si perteneciera al 30/10, no anualiza el rendimiento mensual y no atribuye la variación del patrimonio a pérdidas o reembolsos sin evidencia.

### Tarea 3. Programar la consulta y probar una ejecución (6 minutos)

**Paso 1.** Abrir las acciones del **prompt enviado** en Copilot Chat y seleccionar **Programar este mensaje / Schedule this prompt**. Si no aparece, verificar en [SETUP_GUIDE.md](../SETUP_GUIDE.md) las políticas de experiencias conectadas; no sustituir esta función por Power Automate o un recordatorio de Outlook.

**Paso 2.** Establecer una programación **semanal para los lunes** en un horario permitido por el laboratorio y guardar la configuración. Habilitar notificación por correo únicamente si la organización la permite.

**Paso 3.** Abrir **Configuración y más > Prompts programados / Scheduled prompts**, localizar la tarea en la sección **Activa** y comprobar la periodicidad guardada.

**Paso 4.** Seleccionar **Ejecutar ahora / Run now** para validar la programación sin esperar al lunes; abrir el chat de resultado generado por esa ejecución.

**Paso 5.** Comprobar que esa **nueva ejecución** vuelve a utilizar los archivos A0 y A1. Para considerarla validada, debe devolver las cifras correctas y permitir verificar la procedencia. Si la programación ejecuta texto sin recuperar las fuentes, el resultado es **programación creada, reporte no validado**. No se asegura que los archivos adjuntos en el primer chat persistan en una ejecución automática.

### Tarea 4. Revisar el resultado y cerrar el ejercicio (5 minutos)

**Paso 1.** Comparar la ejecución programada con los valores fuente: patrimonio **124,6 millones USD**, cambio **−1,8 millones USD**; rendimiento acumulado mensual **0,4 %**, cambio **−0,4 puntos porcentuales**; liquidez del **30/10 no disponible**.

**Paso 2.** Identificar dos decisiones de revisión: **solicitar el dato de liquidez del último corte** y **verificar flujos y valoración antes de explicar el cambio del patrimonio**. No aprobar ni difundir el informe como análisis de inversiones.

**Paso 3.** Guardar el resumen corregido dentro de Microsoft 365 si el docente requiere un entregable. Indicar el último corte disponible y que el informe se elaboró con **datos simulados**, no con cotizaciones actuales.

**Paso 4.** Desactivar o eliminar la programación de laboratorio si no existe autorización para dejar una tarea recurrente activa.

### Resultado esperado

Existe un **prompt de Copilot programado semanalmente** y se realizó una prueba mediante **Ejecutar ahora**. Si pudo acceder de nuevo a las fuentes, su reporte muestra patrimonio **124 600 000 USD**, variación **−1 800 000 USD**, rendimiento mensual acumulado **0,4 %**, variación **−0,4 puntos porcentuales** y **liquidez no disponible** para el 30/10/2026. Identifica las fuentes **A0/A1**, no inventa razones ni convierte el dato ausente en cero. **Si la ejecución no accede a los archivos, el reporte automatizado se considera no validado, aun cuando la programación exista.**

Documentación oficial: [Programar prompts de Copilot](https://support.microsoft.com/en-us/microsoft-365-copilot/schedule-your-most-used-copilot-prompts) · [Administrar prompts programados](https://learn.microsoft.com/en-us/copilot/microsoft-365/scheduled-prompts).
