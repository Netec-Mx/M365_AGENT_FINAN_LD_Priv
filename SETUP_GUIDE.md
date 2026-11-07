# Guía general de preparación del entorno

**Curso:** Microsoft 365 Copilot: agentes y aplicaciones para el sector financiero  
**Duración del curso:** 2 horas y 30 minutos; 120 minutos de práctica  
**Alcance:** prácticas 1 a 5 del repositorio; **sin Copilot Studio** como herramienta de desarrollo.

## Descripción del entorno

Se requiere una cuenta institucional de Microsoft 365 con **Microsoft 365 Copilot asignado** (denominado «Premium» en la solicitud del curso), acceso a Copilot Chat y Agent Builder, archivos de práctica en OneDrive o SharePoint, Excel para Microsoft 365 y las funcionalidades habilitadas para cada actividad. Microsoft comercializa el producto como **Microsoft 365 Copilot**; «Premium» no debe interpretarse como la garantía de todas las características de vista previa.

La preparación permite: (1) síntesis en Copilot, (2) conciliación mediante Finance Agent si está habilitado, (3) autoría del agente TLN en Agent Builder, (4) selección de un **Copilot Connector Enterprise Websites realmente indexado y disponible en Agent Builder**, y (5) programación de consultas del Fondo Alfa en Copilot Chat.

## Requisitos de hardware y software

- Equipo con navegador Microsoft Edge o Chrome actualizado y acceso estable a Internet; no se requiere máquina virtual ni infraestructura local adicional.
- Microsoft 365 Copilot en https://m365.cloud.microsoft/chat o la dirección institucional de Microsoft 365 Copilot que resuelva en el inquilino.
- Word y Excel para Microsoft 365 (Web o escritorio) para revisar DOCX/XLSX. Para Finance Agent, verificar **Excel y el complemento efectivo del inquilino**, no asumir que Excel Web ofrece la misma experiencia.
- Sitio de SharePoint y/o OneDrive institucional con capacidad de lectura y escritura según la actividad.

## Licencias, cuentas y permisos

| Función | Condición que debe comprobarse |
|---|---|
| Copilot Chat y Agent Builder | Cuenta institucional con licencia Microsoft 365 Copilot y autoría de agentes permitida por las políticas. |
| Fuentes TLN | Lectura de **F1, F2 y F3** alojados en SharePoint; edición de carpeta solo si el alumno debe cargar los archivos. |
| Finance Agent (práctica 2) | Complemento y opción **Financial Reconciliation** efectivamente disponibles, con condiciones de vista previa/región que apliquen al inquilino. |
| Enterprise Websites (práctica 4) | Administrador con rol **AI Administrator**, conexión publicada e indexada y seleccionable desde Agent Builder para el usuario docente. |
| Prompts programados (práctica 5) | Microsoft 365 Copilot, experiencias conectadas habilitadas y la opción **Schedule this prompt** visible en Copilot Chat (experiencia de trabajo / Work IQ). |
| Datos del fondo | Lectura en la nube del XLSX **A0** y del DOCX **A1**, sin exponer datos financieros reales. |

**Seguridad:** Los documentos TLN y Fondo Alfa son ficticios. No usar archivos de clientes reales, cuentas externas no autorizadas, permisos de administración global innecesarios, secretos o API keys. El conector Enterprise Websites publica páginas públicas en el índice empresarial: su configuración de permisos documentada es **Everyone in the organization**; no usarlo para datos confidenciales.

## Preparación general de los documentos

1. Entrar en SharePoint con la cuenta institucional. Puede utilizarse el sitio `https://azurenetecgp1.sharepoint.com/sites/CopilotSite` **solo si sigue autorizado para el laboratorio**; de lo contrario, usar el sitio que determine el administrador.
2. Identificar en el sitio la **biblioteca real de documentos** por su nombre visible y permisos. No asumir que `Documentos`, `Documentos compartidos` y `Shared Documents` son nombres intercambiables, ni utilizar enlaces abreviados de **Compartir** como rutas del sitio.
3. Preparar dentro de esa biblioteca las carpetas `TLN_Emision` y `Fondo_Alfa`, con lectura autorizada para los participantes. No crear duplicados si ya existen.
4. **Copiar en `TLN_Emision` únicamente los siguientes DOCX** (mismo nombre que en el repositorio):
   - [03_Terminos_indicativos_emision_TLN.docx](Capitulo03/recursos/03_Terminos_indicativos_emision_TLN.docx) (**F1**).
   - [04_Nota_crediticia_TLN.docx](Capitulo03/recursos/04_Nota_crediticia_TLN.docx) (**F2**).
   - [07_Minuta_revision_preliminar_TLN.docx](Capitulo03/recursos/07_Minuta_revision_preliminar_TLN.docx) (**F3**).
5. **Copiar en `Fondo_Alfa`** el archivo [Indicadores_Fondo_Alfa.xlsx](Capitulo03/recursos/Indicadores_Fondo_Alfa.xlsx) (**A0**) y la ficha [08_Contexto_y_control_Fondo_Alfa.docx](Capitulo03/recursos/08_Contexto_y_control_Fondo_Alfa.docx) (**A1**).
6. Verificar que cada archivo puede abrirse desde **SharePoint o OneDrive** con la identidad que ejecutará la actividad, y que las fuentes de TLN **no se mezclan** con las del fondo.
7. Mantener disponibles también los recursos iniciales de [Capítulo 1](Capitulo01/README.md) y [Capítulo 2](Capitulo02/README.md); no sustituir sus materiales por archivos web externos.

## Preparación de las aplicaciones

### 1. Microsoft 365 Copilot y fuentes de trabajo

1. Abrir Copilot Chat y comprobar que acepta preguntas y referencias a documentos en la nube.
2. Revisar la disponibilidad de la experiencia de cuadernos o áreas de trabajo del capítulo 1, con capacidad de incorporar archivos del caso. Los nombres de las superficies pueden variar por actualización del producto.
3. En Microsoft 365 Copilot, localizar **Nuevo agente**, la pestaña **Configurar** y la sección **Conocimiento**. Comprobar que puede seleccionarse un archivo de SharePoint, sin crear todavía el agente definitivo.
4. No habilitar el portal de Copilot Studio ni exigir licencias de Copilot Studio para las prácticas 3–5.

**Documentación:** https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents y https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge

### 2. Finance Agent (práctica 2)

1. Abrir Excel para Microsoft 365 con la cuenta asignada.
2. Confirmar que el complemento **Finance Agent** está disponible y que ofrece **Financial Reconciliation / Conciliación financiera**.
3. Comprobar las restricciones de disponibilidad regional, vista previa y directivas del inquilino indicadas por Microsoft. **La sola licencia Microsoft 365 Copilot no garantiza Finance Agent.**
4. Si falta la función, informar que la práctica 2 **no puede ejecutarse con la tecnología prevista**; no afirmar que una conciliación manual es una ejecución de Finance Agent.

**Documentación:** https://learn.microsoft.com/en-us/copilot/finance/get-started/deployment-guide

### 3. Enterprise Websites — preparación del administrador (práctica 4)

Esta sección se realiza **antes de la clase**. Los 5 minutos de práctica no alcanzan para rastrear e indexar un sitio web.

1. Acceder a https://admin.microsoft.com/ con rol **AI Administrator**, abrir **Copilot > Connectors > Gallery** y seleccionar **Enterprise Websites / Sitio web empresarial**.
2. Crear una conexión con nombre de referencia **`FinanzasWebCurso`** (o registrar un nombre diferente y sustituirlo en los prompts). Elegir **una** URL pública de la lista, en este orden de prueba: [Banco Mundial](https://www.worldbank.org/), [BID](https://www.iadb.org/) e [Investopedia](https://www.investopedia.com/). Son **sitios candidatos, no validados automáticamente**.
3. Utilizar autenticación **None** para páginas públicas sin inicio de sesión; configurar el alcance y el rastreo del sitio de acuerdo con las opciones disponibles. Si se habilita rastreo por sitemap, verificar que el sitemap contiene páginas relevantes. Las redirecciones aceptadas por el conector son **dentro del mismo hostname**.
4. Publicar la conexión y verificar **elementos indexados con contenido** en **Your connections**. Una conexión creada o una página que abre en el navegador no prueban que el rastreador la haya indexado. Los sitios con desafío anti-bot, redirección a otro dominio, restricciones de `robots.txt` o contenido dinámico no compatible pueden fallar.
5. Abrir Agent Builder con la cuenta del instructor, entrar en **Configurar > Conocimiento > Elegir otros orígenes de datos**, comprobar que **la conexión real** puede agregarse y realizar una consulta de prueba con **una cita abierta**. Una conexión visible solo en el portal administrativo **no satisface** el objetivo de la práctica 4.
6. Seleccionar un solo sitio funcional para la clase y dejar el resto como alternativas descartables. Si ninguno se indexa o aparece en Agent Builder, **no declarar la práctica como ejecutable** y no reemplazar silenciosamente el conector por **Búsqueda en la web**.

**Recursos:** [05_Fuentes_web_financieras.md](Capitulo03/recursos/05_Fuentes_web_financieras.md) y [06_Validacion_conector_web.md](Capitulo03/recursos/06_Validacion_conector_web.md).

**Información que debe conocer el docente:** Enterprise Websites es un **conector sincronizado de conocimiento**, no una herramienta de Power Platform. Su contenido no es necesariamente el más reciente, no modifica sistemas externos, no valida automáticamente las cifras del emisor TLN y puede mostrarse en Microsoft Search o Microsoft 365 Copilot según las opciones del servicio.

**Documentación:** https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/enterprise-web-connector y https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/manage-connector

### 4. Prompts programados (práctica 5)

1. Entrar en **Copilot Chat con la experiencia de trabajo (Work IQ)** y comprobar que una indicación enviada muestra **Programar este mensaje / Schedule this prompt**. Microsoft documenta esta disponibilidad en la experiencia de trabajo, no en cualquier pantalla de Copilot.
2. Comprobar que **Configuración y más > Prompts programados / Scheduled prompts** está disponible y que la política de **experiencias conectadas** no está bloqueada. La documentación de administración indica que estas experiencias se gestionan bajo **Connected Experiences** a partir de agosto de 2026.
3. Verificar que los archivos A0 y A1 pueden referenciarse por nombre y abrirse desde la nube con el usuario de la práctica.
4. No programar una tarea antes del ejercicio. La práctica enseñará a utilizar **Ejecutar ahora** y a verificar que una nueva ejecución **recupera realmente las fuentes**; no se debe prometer persistencia de adjuntos ni actualización automática del Excel.

**Documentación:** https://support.microsoft.com/en-us/microsoft-365-copilot/schedule-your-most-used-copilot-prompts y https://learn.microsoft.com/en-us/copilot/microsoft-365/scheduled-prompts

## Verificación de preparación antes de impartir

| Comprobación | Criterio de aceptación | Si falla |
|---|---|---|
| Copilot Chat | Abre y consulta fuentes institucionales | Revisar licencia, política o cuenta |
| Capítulo 1 | Experiencia de organización de fuentes visible | Confirmar superficie habilitada |
| Finance Agent | **Financial Reconciliation** operativo en Excel | Práctica 2 bloqueada en la tecnología solicitada |
| Agent Builder | **Nuevo agente**, **Configurar** y selección de SharePoint | Práctica 3 bloqueada; no usar Copilot Studio |
| F1, F2 y F3 | Se abren desde SharePoint; mismo expediente | Revisar permisos y ubicación |
| Conector web | Contenido indexado y **visible/probado en Agent Builder** | Práctica 4 no validada; preparar otro sitio antes de clase |
| Prompts programados | Opción disponible en Copilot Chat de trabajo | Práctica 5 no puede comprobar recurrencia |
| A0 y A1 | Abrir, leer y contrastar desde Microsoft 365 | Revisar rutas, permisos y disponibilidad |

## Consideraciones adicionales y cierre

- **Se trata de escenarios distintos:** TLN es el emisor ficticio de las prácticas 1, 3 y 4; Fondo Alfa Capital es el fondo ficticio de la práctica 5; el libro de conciliación TLN de la práctica 2 utiliza un conjunto de movimientos diferente al expediente de bonos.
- **No mezclar fuentes:** Los sitios Banco Mundial, BID o Investopedia aportan contexto público; no contienen ni certifican los números privados simulados de TLN.
- **No simular capacidades ausentes:** un agente sin conexión empresarial verificable no demuestra el conector; un prompt programado sin acceso a fuentes no constituye un seguimiento automatizado validado.
- **Limpieza:** desactivar o eliminar la programación de prueba si no se requiere mantenerla y respetar las políticas de almacenamiento y eliminación de datos del sitio.
- **No hay costo de infraestructura adicional previsto** para crear estos archivos. La disponibilidad de servicios y las condiciones de licencia del inquilino se deben confirmar con el administrador, sin activar modalidades de pago por uso sin autorización.
