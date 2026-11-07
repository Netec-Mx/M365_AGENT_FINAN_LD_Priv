# Práctica 1. Selección de asistencia y síntesis de un caso financiero

## Objetivo de la práctica:

Al finalizar la práctica, serás capaz de:

- Seleccionar entre un **prompt directo**, un **cuaderno/área de trabajo de Copilot** y un **agente** para necesidades financieras delimitadas.
- Sintetizar información sectorial simulada con referencias verificables a los documentos de origen.
- Preparar una **ficha de vinculación** y el **esquema de una presentación**, distinguiendo producción de contenido y revisión humana.

## Duración aproximada:

- **22 minutos.**

## Tabla de ayuda:

| Parámetro | Valor | Uso |
|---|---|---|
| Organización del caso | Transportes Logísticos del Norte S.A. (**TLN**) | Empresa ficticia por analizar. |
| Fuente S1 | [01_Perfil_y_datos_TLN.docx](recursos/01_Perfil_y_datos_TLN.docx) | Perfil y cifras corporativas. |
| Fuente S2 | [02_Nota_sectorial_TLN.docx](recursos/02_Nota_sectorial_TLN.docx) | Factores y riesgos del escenario sectorial. |
| Aplicación de Copilot | [m365.cloud.microsoft](https://m365.cloud.microsoft/) | Chat y cuadernos/Workspaces. |
| Herramienta de edición | Word para Microsoft 365 | Consolidar los productos finales. |
| Nombre del espacio | `TLN - Analisis y vinculacion` | Identificar las referencias de la práctica. |

> **Importante:** Microsoft ha comenzado a mostrar **Copilot Workspaces** donde antes se mostraban **Notebooks / Cuadernos**. Usar la opción que permita **agregar referencias** y consultar su contenido. No confundir un cuaderno con el bloc de notas convencional de OneNote.

## Instrucciones

### Tarea 1. Inspeccionar las fuentes y elegir la forma de asistencia (4 minutos)

**Paso 1.** Descargar los archivos **S1** y **S2** desde la Tabla de ayuda, abrirlos y comprobar el nombre de la organización, los periodos de las cifras y el aviso de simulación.

**Paso 2.** Abrir **Copilot Chat**, iniciar una conversación de trabajo e introducir el siguiente mensaje. No adjuntar todavía los documentos: se quiere observar qué puede y qué no puede resolver una consulta sin contexto.

**Prompt 1 — Solicitud inicial sin fuentes**

```text
Actúa como analista de vinculación corporativa. Necesito preparar un resumen
financiero y sectorial de Transportes Logísticos del Norte S.A. (TLN).
No tienes documentos de esta entidad en el mensaje. Indica solamente qué
información necesitarías para construir una ficha de cliente y una presentación
para un comité. No inventes cifras, verificaciones KYC ni características
específicas de la empresa.
```

**Paso 3.** Verificar que el mensaje de Copilot no demuestra cifras ni validaciones de TLN sin un documento que las respalde. Si aparecen datos inventados, identificarlos como no utilizables.

**Paso 4.** Utilizar este criterio para seleccionar el mecanismo que corresponde a cada necesidad de la práctica:

| Necesidad del caso | Elección | Justificación |
|---|---|---|
| Preguntar qué información falta para vincular a TLN | **Prompt directo** | Petición puntual sin conocimiento persistente. |
| Combinar S1 y S2 para obtener resumen y materiales basados en fuentes | **Cuaderno / Workspace** | Organiza referencias de un proyecto y permite comprobar sus contenidos. |
| Resolver en sesiones sucesivas preguntas estandarizadas sobre la operación | **Agente personalizado** | Reutiliza instrucciones y fuentes delimitadas; se desarrollará en la práctica 3. |

La selección es parte de la actividad, no exige crear el agente en este módulo.

### Tarea 2. Organizar las fuentes y generar una síntesis contrastable (8 minutos)

**Paso 1.** Entrar en **Notebooks / Cuadernos / Workspaces** desde la aplicación Copilot y crear uno con el nombre `TLN - Analisis y vinculacion`.

**Paso 2.** Seleccionar **Agregar referencias / Add references** y cargar **S1** y **S2**. Si la experiencia exige que los archivos estén en OneDrive o SharePoint, guardarlos primero en la ubicación de laboratorio autorizada y seleccionarlos desde ella.

**Paso 3.** Confirmar que aparecen ambas referencias en el área de trabajo y que es posible abrirlas. No utilizar referencias públicas adicionales: el caso solo aporta S1 y S2.

**Paso 4.** Formular la siguiente consulta dentro del espacio con las dos referencias disponibles.

**Prompt 2 — Síntesis financiera y sectorial fundamentada**

```text
Utiliza exclusivamente S1 / Perfil TLN y S2 / Sector TLN, ya agregados a
este cuaderno o área de trabajo. Devuelve:
1. Descripción del negocio de TLN en máximo 70 palabras.
2. Tabla con ingresos de 2024 y 2025, EBITDA de 2024 y 2025 y márgenes.
3. Variación porcentual de ingresos entre 2024 y 2025; muestra el cálculo.
4. Tres riesgos o aspectos por investigar para la vinculación.
5. Dos datos que NO pueden verificarse con las fuentes disponibles.
Indica al lado de cada dato si procede de S1 o S2 y distingue los cálculos
propios de los valores que figuran textualmente en las fuentes. No consultes
fuentes externas ni afirmes que el KYC está aprobado.
```

**Paso 5.** Contrastar con **S1** que los ingresos son **42 500 000 USD en 2024** y **48 200 000 USD en 2025**, y que el EBITDA es **8 500 000** y **10 122 000 USD**, respectivamente. La variación de ingresos es aproximadamente **13,4 %**: `(48 200 000 - 42 500 000) / 42 500 000 × 100`.

**Paso 6.** Contrastar con **S2** que los riesgos del escenario son cualitativos y que no hay tamaño de mercado ni estadísticas públicas. Corregir en la conversación cualquier cifra que no exista en los documentos y repetir la síntesis si es necesario.

### Tarea 3. Elaborar la ficha y el esquema de presentación (6 minutos)

**Paso 1.** Mantener abierto el cuaderno con S1 y S2. Introducir el siguiente mensaje, solicitando dos artefactos breves.

**Prompt 3 — Ficha y esquema para vinculación**

```text
Conserva únicamente las fuentes S1 y S2 del caso TLN. Prepara en español:
A. Una ficha de vinculación preliminar (no una ficha KYC aprobada) con:
   empresa, sector, ubicación, segmentos comerciales, ventas 2025,
   EBITDA 2025, riesgos sectoriales y comprobaciones documentales pendientes.
B. El esquema de una presentación de cuatro diapositivas para un comité:
   1) perfil y operación; 2) cifras 2024-2025; 3) riesgos sectoriales;
   4) preguntas abiertas para decidir próximos pasos de vinculación.
En cada sección indica S1 o S2 para que pueda contrastarse el contenido.
No declares que se investigaron listas restrictivas, beneficiarios finales,
auditorías o calificaciones externas. Señala "no documentado" cuando proceda.
```

**Paso 2.** Crear en **Word para Microsoft 365** un documento denominado `Ficha_y_esquema_TLN.docx` y pegar la ficha y el esquema obtenidos. El entregable es el **esquema**; no es necesario construir una presentación PowerPoint completa.

**Paso 3.** Revisar que la ficha no afirma aprobaciones KYC inexistentes. Verificar la correspondencia de cada cifra con S1 y de cada factor sectorial con S2; corregir el documento si aparece una inferencia no sustentada.

### Tarea 4. Distinguir generación de revisión humana y confirmar el resultado (4 minutos)

**Paso 1.** Comparar la respuesta del **Prompt 1** (sin documentos) con la ficha elaborada a partir de **S1 y S2**. Identificar qué elementos solo pudieron generarse con referencias adjuntas.

**Paso 2.** Revisar el documento Word y distinguir las acciones de **elaboración** (resumir, estructurar) de las de **validación** (abrir las fuentes, cotejar cifras, corregir afirmaciones). Si se registraron los tiempos, indicar que la rapidez de la primera no elimina la segunda; no es necesario generar una bitácora.

**Paso 3.** Guardar `Ficha_y_esquema_TLN.docx` y comprobar que contiene la ficha, el esquema de cuatro diapositivas, las etiquetas S1/S2 y los datos faltantes marcados con claridad.

### Resultado esperado

El participante dispone de un cuaderno o área de trabajo con las dos fuentes del caso TLN y un documento **`Ficha_y_esquema_TLN.docx`** que contiene una ficha preliminar y un esquema de cuatro diapositivas. Las cifras 2024–2025 coinciden con S1; los riesgos se atribuyen a S2; y las verificaciones KYC no aportadas se identifican como pendientes. Puede explicar por qué un prompt puntual, un cuaderno y un agente resuelven necesidades diferentes, y por qué la revisión documental sigue siendo obligatoria.

Documentación de referencia: [Agregar referencias a Copilot Notebooks](https://support.microsoft.com/en-us/microsoft-365-copilot/add-references-to-your-microsoft-365-copilot-notebook) · [Transición a Copilot Workspaces](https://support.microsoft.com/en-us/microsoft-365-copilot/copilot-notebooks-to-copilot-workspaces).
