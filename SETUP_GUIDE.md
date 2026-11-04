# Setup Guide General

## Microsoft 365 Copilot: agentes y aplicaciones para el sector financiero

| Control documental | Información |
|---|---|
| Repositorio | [Netec-Mx/M365_AGENT_FINAN_LD_Priv](https://github.com/Netec-Mx/M365_AGENT_FINAN_LD_Priv) |
| Rama y revisión analizada | `main` — `b2e92a12971313e16a9d66e79503201e95a22132` |
| Alcance revisado | Tres capítulos; cinco actividades, incluida una demostración del instructor; README principal, SETUP_GUIDE.md, CODEOWNERS e inventario de recursos |
| Versión documental | 1.0 |
| Fecha de revisión | 3 de noviembre de 2026 |
| Modalidad | Windows, aplicaciones Microsoft 365 de escritorio, servicios web y entorno cloud administrado |

# Objetivo

Preparar un entorno único para trabajar con Microsoft 365 Copilot, Finance Agent en Excel y un agente de Copilot Studio fundamentado en documentos de SharePoint, con permisos, formatos y almacenamiento comprobados antes del curso.

El entorno estará listo cuando la cuenta del participante pueda utilizar las aplicaciones, abrir Finance Agent, acceder a las fuentes autorizadas y crear, probar y publicar agentes en el entorno asignado. Esta guía contiene prerrequisitos, preparación y validación; no desarrolla los ejercicios ni genera sus entregables.

El repositorio distribuye documentación y un logotipo. No incluye instaladores, manifiestos del complemento, soluciones de Copilot Studio, archivos Office, CSV o fuentes financieras descargables. Los generadores de datos y las instrucciones para crear esos archivos están incorporados en los README.

# Requisitos de Hardware

El repositorio no fija RAM, CPU, espacio libre ni resolución mínimos. Para preparar la estación se toma como referencia la compatibilidad de Microsoft 365 Apps y se distingue de la recomendación operativa para el taller.

| Recurso | Base de compatibilidad | Recomendación de preparación |
|---|---|---|
| Procesador | Compatible con Windows 11 y aplicaciones de 64 bits; Microsoft 365 indica 1.6 GHz y dos núcleos | Equipo capaz de mantener Excel y varias pestañas del navegador simultáneamente |
| Memoria | Microsoft 365 Apps de 64 bits: 4 GB | 8 GB o más; 16 GB si se utilizan varias aplicaciones a la vez |
| Espacio libre | Microsoft 365 Apps: 4 GB para su instalación; el sistema operativo requiere su propio espacio | Reservar espacio adicional para actualizaciones, documentos y descargas |
| Pantalla | Microsoft 365 Apps: 1280 × 768 | 1920 × 1080 para comparar Excel, fuentes y paneles de agentes |
| Conectividad | Internet estable durante toda la sesión | HTTPS y endpoints de Microsoft 365, Finance Agent y Copilot Studio permitidos |

Las recomendaciones no son mínimos publicados por el repositorio. No se necesita GPU ni hardware de virtualización.

# Sistemas Operativos Compatibles

La ruta documentada utiliza **Windows 11**, directorios `C:\Labs\...`, aplicaciones Microsoft 365 de escritorio y PowerShell. Utilizar Windows 11 de 64 bits, en una edición y compilación con soporte vigente; Enterprise aparece como referencia en el material, pero no se demuestra una dependencia exclusiva de esa edición.

No se incluyen procedimientos para Linux o macOS porque el repositorio no desarrolla esas rutas. La disponibilidad web de algunos servicios no convierte por sí sola toda la secuencia de Excel y archivos locales en una ruta multiplataforma validada.

# Software Requerido

| Componente | Versión o criterio consolidado | Uso necesario |
|---|---|---|
| Microsoft Excel para Microsoft 365 | 64 bits, canal institucional con soporte; referencia de preparación disponible al revisar: Current Channel 2610, build 20527.20112 | Importación CSV, tablas, fórmulas, archivos XLSX y complemento Finance Agent |
| Microsoft Word para Microsoft 365 | Aplicación de escritorio activada; mismo despliegue Office administrado | Guardado DOCX y conversión de fuentes a documentos compatibles |
| Microsoft PowerPoint para Microsoft 365 | Aplicación de escritorio activada | Guardado y edición de presentaciones |
| Microsoft 365 Copilot | Servicio administrado, con licencia asignada y acceso corporativo | Chat, fuentes adjuntas o referenciadas y capacidades organizacionales del curso |
| Finance Agent para Excel | Complemento oficial de Microsoft disponible y habilitado para el usuario | Conciliación asistida en Excel; confirmar la experiencia realmente desplegada |
| Microsoft Copilot Studio | Servicio web, experiencia compatible con las secciones de agente, instrucciones y conocimiento | Creación, prueba y publicación de agentes |
| Microsoft SharePoint Online | Servicio organizacional | Biblioteca documental y carpeta de informes |
| Microsoft Dataverse | Entorno administrado utilizado por Copilot Studio | Almacenamiento y funcionamiento del entorno de agentes |
| Microsoft Edge | Versión estable vigente de 64 bits; cumple el mínimo de Copilot Studio —122 o posterior— y de Finance Agent web —Chromium 120 o posterior— | Acceso web y autenticación |
| PowerShell | PowerShell 7.x con soporte, mínimo 7.4 para unificar la ruta; instalar el parche mantenido de la rama elegida | Carpetas, fuentes de texto y comprobaciones locales |
| Editor de texto UTF-8 | Bloc de notas o editor institucional equivalente | Archivos TXT y Markdown; VS Code es opcional |

La referencia de Office es una base de preparación, no una certificación de prueba del tenant ni una obligación de degradar una versión posterior compatible. Una organización con otro canal soportado debe validar Finance Agent y las operaciones de Excel en ese despliegue y registrar su compilación real.

Windows PowerShell 5.1 puede ejecutar los comandos de archivos mostrados, pero no se instala automáticamente PowerShell 7 junto con Windows. Para conservar una sola ruta común, utilizar PowerShell 7 y evitar alternar terminales sin registrar su versión.

No se requieren Python, Java, .NET SDK, Node.js, IDE, Azure CLI, módulos Microsoft Graph/PnP, Docker, Kubernetes, máquinas virtuales ni emuladores. El uso de JSON, Markdown, fórmulas y PowerShell no implica instalar un framework de desarrollo.

# Herramientas y Dependencias

## Licencias y acceso corporativo

| Capacidad | Requisito que debe resolver TI |
|---|---|
| Microsoft 365 Apps | Suscripción que incluya las aplicaciones de escritorio utilizadas, activadas para la cuenta del participante |
| Microsoft 365 Copilot | Complemento o derecho de uso vigente sobre una suscripción base elegible; el chat básico por sí solo no acredita toda la ruta documentada |
| Finance Agent | Complemento oficial asignado y condiciones de uso/licencia vigentes confirmadas para esa experiencia |
| Copilot Studio completo | Derechos de autoría y publicación, acceso al entorno, capacidad y condiciones de consumo resueltas |
| SharePoint Online | Sitio y biblioteca disponibles, con lectura y escritura de documentos |

El material exige E5 en un apartado, pero los requisitos oficiales de despliegue de Finance Agent no establecen E5 como único plan posible. No comprar ni dar por suficiente E5 únicamente por esa mención: confirmar el conjunto de aplicaciones, Copilot y Finance Agent habilitado en las cuentas reales.

La documentación de Finance Agent consultada describe condiciones de vista previa y sus derechos asociados al despliegue. No se garantiza que sean permanentes ni que una compilación histórica del complemento siga distribuida. TI debe registrar la oferta y condiciones efectivas del tenant antes de impartir.

Una prueba de Copilot Studio permite crear y probar agentes, pero no publicarlos según la documentación vigente. Como el repositorio incluye publicación, no considerar completo el setup con una cuenta trial que solo accede al panel de pruebas. Validar los derechos aplicables a la publicación prevista, sin activar suscripciones por consumo durante la sesión para resolver errores.

## Identidades y permisos

- Cuenta nativa de Microsoft Entra ID del tenant de laboratorio, con las licencias asignadas; no utilizar cuentas personales ni invitados externos para Finance Agent.
- Permiso de escritura en `C:\Labs\M365_Copilot_Finance\`.
- Acceso al entorno de Copilot Studio y roles de autoría correspondientes, por ejemplo Environment Maker y los roles Dataverse que requiera la configuración institucional.
- Permiso para crear, guardar, probar y publicar el agente propio; no se necesita administrador global para participar.
- Lectura de las fuentes de SharePoint y edición en la biblioteca/carpeta de laboratorio para cargar documentos e informes.
- Acceso del instructor a su agente y fuentes para la demostración, sin depender de la sesión del estudiante.

Los valores `estudianteXX@contosofinance.onmicrosoft.com` y `https://contosofinance.sharepoint.com/sites/MercadoCapitales` son referencias del material, no recursos aprovisionados por GitHub. Sustituirlos por las identidades y URL que TI entregue. No intentar iniciar sesión en un tenant ajeno.

## Dependencias de Finance Agent y alcance

Se utiliza la conciliación **asistida** del complemento de Excel. No se requieren Dynamics 365 Finance, SAP, Business Central, un ERP real ni una conexión bancaria: el supuesto libro mayor y el extracto son archivos locales generados por el material.

La solución autónoma de Finance Agent, sus plantillas y sus acciones programadas tienen un aprovisionamiento adicional. No instalar esos componentes solo por el nombre «Agent» si la actividad utiliza el panel asistido. El entorno Dataverse de Copilot Studio sí debe estar preparado para la autoría del agente personalizado.

Finance Agent, Copilot general de Excel y las nuevas capacidades financieras o skills de Copilot no deben tratarse como superficies idénticas. La pantalla requerida debe verificarse antes del curso. Si el tenant ofrece otra experiencia, adaptar y ensayar la copia de trabajo con el instructor; no marcar automáticamente como disponible el procedimiento original.

# Instalación y Configuración

## 1. Preparar Windows y las aplicaciones

1. Confirmar Windows 11 de 64 bits y las actualizaciones institucionales.
2. Instalar Microsoft 365 Apps de 64 bits mediante el paquete o portal autorizado de la organización. Incluir Excel, Word y PowerPoint.
3. Abrir cada aplicación e iniciar sesión con la cuenta del laboratorio. Confirmar activación desde **Archivo > Cuenta**.
4. Aplicar la versión admitida por TI y registrar canal, versión, compilación y arquitectura desde **Acerca de Excel**.
5. En Excel, comprobar **Datos > Obtener datos > Desde texto/CSV**, creación de tablas y cálculo automático.
6. Actualizar Edge y comprobar copiado/pegado, descargas y autenticación corporativa.

No instalar el build 2408 del repositorio para intentar dar una versión a Copilot Chat. Las compilaciones de Office y el servicio de Copilot se administran por separado.

## 2. Instalar PowerShell si falta

Utilizar el paquete institucional. Si WinGet está autorizado, el siguiente comando instala la edición estable mediante MSI:

```powershell
winget install --id Microsoft.PowerShell --exact --source winget --installer-type wix
```

Abrir una nueva sesión y verificar:

```powershell
& 'C:\Program Files\PowerShell\7\pwsh.exe' -NoProfile -Command '$PSVersionTable.PSVersion'
```

La ruta anterior corresponde a la instalación MSI estándar. Si TI eligió otro método, consultar `Get-Command pwsh` y usar la ruta realmente instalada.

Los comandos interactivos de creación de archivos no necesitan `Set-ExecutionPolicy Unrestricted`. Conservar la política institucional. Si se distribuyen archivos `.ps1`, utilizar el mecanismo de firma o ejecución autorizado por TI.

## 3. Desplegar Finance Agent para Excel

Realizar antes del curso, preferentemente por el administrador:

1. Entrar al [Centro de administración de Microsoft 365](https://admin.microsoft.com/).
2. Ir a **Configuración > Aplicaciones integradas > Obtener aplicaciones**.
3. Buscar la aplicación oficial **Finance in Microsoft Copilot** para Excel y comprobar que el editor sea Microsoft.
4. Asignar el complemento al grupo de participantes y revisar sus permisos mediante el procedimiento institucional.
5. Finalizar el despliegue y comprobarlo con una cuenta asignada.

Microsoft indica que la aparición del complemento puede tardar hasta seis horas; no dejar su despliegue para el inicio de la sesión. La instalación individual desde Marketplace solo es una alternativa si la política del tenant la permite.

En Excel, abrir un libro temporal con dos tablas pequeñas, localizar Finance Agent —la documentación actual lo sitúa en Inicio— y comprobar que aparece **Financial Reconciliation** y permite seleccionar ambas tablas. El botón no tiene por qué coincidir con las pestañas descritas en el material antiguo.

No es necesario instalar el complemento de Outlook ni configurar cobros o integración ERP para esta ruta.

## 4. Preparar Copilot Studio y Dataverse

TI debe proporcionar un entorno de laboratorio habilitado para Copilot Studio, con Dataverse, región compatible con las capacidades de IA utilizadas, permisos de autoría y publicación y capacidad suficiente para las pruebas.

1. Abrir [Copilot Studio](https://copilotstudio.microsoft.com/) con la cuenta organizacional.
2. Seleccionar el entorno comunicado por TI y registrar nombre e identificador.
3. Confirmar que está disponible la creación del agente con instrucciones, conocimiento y panel de pruebas de la experiencia estándar utilizada por el material.
4. Comprobar que SharePoint puede añadirse como conocimiento y que las políticas de datos no bloquean su uso.
5. Confirmar que la cuenta puede publicar un agente temporal de validación en el entorno autorizado.

No crear un entorno distinto ni pasar a otro tenant para eludir un error. No es necesario desplegar una base SQL, una VM o recursos propios en Azure. Dataverse es un servicio administrado del entorno.

## 5. Habilitar SharePoint y autenticación

El administrador debe proporcionar la URL real del sitio, la biblioteca y sus permisos. Se mantiene el nombre lógico `MercadoCapitales` si se crea un sitio específico para el taller.

Preparar una ubicación para las fuentes de conocimiento y la carpeta **InformesFinancieros** para los reportes. En sitios compartidos, separar las fuentes por participante o equipo para evitar que documentos homónimos o variantes de prueba se mezclen en la recuperación.

Para la integración descrita, utilizar **SharePoint como fuente de conocimiento por URL** y autenticación de usuario con Microsoft. No confundirla con cargar una copia estática desde el disco ni con agregar una acción del conector SharePoint a una herramienta.

La autenticación debe conservar los permisos del usuario. No configurar **Sin autenticación** para resolver fallos ni usar credenciales de un propietario con acceso más amplio. El recorrido habitual no necesita que cada estudiante registre una aplicación Entra o administre secretos; si el cliente elige autenticación manual o un canal distinto, TI debe preparar y validar esa variante previamente.

# Configuración Base para los Laboratorios

## Directorios locales

Ejecutar en PowerShell con permiso de escritura sobre la ruta. TI puede crear la raíz y conceder escritura al usuario antes de la sesión; no es necesario trabajar siempre como administrador.

```powershell
$labRoot = 'C:\Labs\M365_Copilot_Finance'
$subfolders = @('Lab01_Fuentes', 'Lab02_Conciliacion', 'Lab03_Agente')

New-Item -ItemType Directory -Force -Path $labRoot -ErrorAction Stop | Out-Null
foreach ($subfolder in $subfolders) {
    New-Item -ItemType Directory -Force -Path (Join-Path $labRoot $subfolder) -ErrorAction Stop | Out-Null
}
Get-ChildItem -LiteralPath $labRoot -Directory | Select-Object Name, FullName
```

Estructura común:

```text
C:\Labs\M365_Copilot_Finance\
├── Lab01_Fuentes\
├── Lab02_Conciliacion\
└── Lab03_Agente\
```

Los libros y reportes del seguimiento se guardan en la raíz según el material. No se requiere una carpeta adicional por actividad. Si TI necesita usar otra unidad o el perfil del usuario, sustituir todas las rutas absolutas del material de forma coherente antes de la sesión.

## Archivos de entrada y formatos

| Familia de archivos | Formato de trabajo | Preparación necesaria |
|---|---|---|
| Fuentes de perfil, estados y riesgo | TXT UTF-8 | Se generan con los bloques del repositorio; Copilot debe recibir el texto o un adjunto explícito. |
| Datos tabulares | CSV UTF-8 con separador coma y punto decimal | Importar mediante el asistente de datos y comprobar tipos antes de guardarlos como XLSX. |
| Libros de trabajo | XLSX con tablas de Excel reales | Conservar los nombres `Tabla_ERP`, `Tabla_Banco`, `Tabla_Modelo` y `Tabla_KPIs_Alfa` cuando se creen. |
| Fuentes de conocimiento de bonos | DOCX y PDF con texto seleccionable | Convertir las fuentes TXT a documentos compatibles antes de subirlas a la integración de SharePoint por URL. |
| Informes y plantillas de texto | MD o TXT UTF-8 | Editor de texto autorizado; pueden almacenarse en SharePoint sin que eso los convierta automáticamente en fuentes de conocimiento compatibles. |

**Corrección de formato necesaria:** el material genera dos TXT, aunque sus constantes ya nombran `TermSheet_Bonos_EnergyCorp_2025.docx` y `Prospecto_Emision_EnergyCorp_vFinal.pdf`. La integración de SharePoint por URL documenta DOC/DOCX, PPT/PPTX y PDF. Para esa ruta, abrir el contenido en Word y guardar un DOCX real y exportar un PDF real con esos nombres, sin alterar el contenido. Actualizar en las copias de trabajo los pasos de carga y las referencias de archivos a los formatos definitivos. No cambiar solo la extensión.

La carga directa de TXT al agente puede tener otro soporte de formatos, pero no sustituye la demostración de acceso delegado al documento original en SharePoint.

## Importación, idioma y codificación

- Importar CSV con codificación UTF-8 y delimitador coma. No depender de la apertura por doble clic y de los separadores regionales de Windows.
- En Power Query, establecer importes y ratios como números decimales utilizando una configuración regional compatible con el punto decimal del archivo; fechas con formato año-mes-día.
- Guardar los libros como XLSX. Convertir porcentajes mediante formato de celda; no volver a multiplicar una fracción solo para mostrarla.
- Usar fórmulas localizadas de Excel: el material muestra nombres en español; una instalación en inglés puede requerir sus equivalentes. Mantener el cálculo automático.
- Para contenido literal de PowerShell que incluya signos `$`, comillas o backticks, utilizar here-strings de comilla simple —apertura `@'` y cierre `'@` en líneas separadas—. Los here-strings de comilla doble del material pueden interpolar importes como si fueran variables y modificar las fuentes.

No eliminar ni «corregir» datos del caso para conseguir que una comprobación técnica pase. La validación del setup acredita lectura, tipos y capacidad de ejecución, no certifica cifras contables o resultados de IA del ejercicio.

## Registro común del entorno

Conservar un registro sin secretos con: cuenta de laboratorio, etiqueta/licencia visible de Copilot, canal/build Office, versión de PowerShell y Edge, nombre/ID del entorno de Studio, URL del sitio, biblioteca, carpeta de fuentes, carpeta de informes y aplicación Finance Agent asignada.

No se requiere `.env`, variable de entorno persistente, token de API, cadena de conexión local ni archivo de configuración de un proyecto. `$labRoot`, `$LabDir` y los contenidos de los generadores son variables de sesión. El acceso cloud se gestiona mediante la autenticación institucional.

## Conservación de recursos y alcance de la recurrencia

Conservar el agente y sus documentos hasta terminar la demostración que los reutiliza. La limpieza que elimina el agente, la carpeta `Lab03_Agente` y las fuentes de SharePoint debe trasladarse al cierre final autorizado del taller. La copia del instructor debe permanecer operativa durante su demostración.

Aunque los metadatos citan Power Automate y seguimiento recurrente, los pasos publicados ejecutan manualmente un prompt en Copilot y cargan el informe mediante navegador. No crean un flujo, un disparador ni una tarea programada. **Power Automate no es necesario para ejecutar esos pasos tal como están escritos.**

La programación automática queda fuera del procedimiento implementado. Si el alcance de impartición exige una recurrencia real, el instructor debe proporcionar antes una ruta adicional validada, sus permisos, licencia y mecanismo de programación. No declarar probada una automatización por haber guardado un prompt o ejecutado una consulta manual, ni añadir conectores Premium o un servicio de scheduling sin esa definición.

# Servicios Externos Requeridos

| Servicio | Acceso necesario |
|---|---|
| Microsoft Entra ID | Identidad del laboratorio y autenticación requerida por el tenant |
| Microsoft 365 Copilot | Acceso corporativo en [copilot.cloud.microsoft](https://copilot.cloud.microsoft/) o la entrada vigente publicada por TI |
| Microsoft 365 Apps | Activación, actualizaciones y servicios conectados de Office |
| Finance Agent / Marketplace | Distribución del complemento y servicio de conciliación habilitado |
| Copilot Studio / Power Platform / Dataverse | Autoría, conocimiento, pruebas y publicación |
| SharePoint Online | Sitio, biblioteca y permisos de fuentes e informes |
| GitHub | Consulta o descarga de las guías públicas |

No se requieren EMIS, Capital IQ, Bloomberg, datos bursátiles en vivo, SAP o un ERP productivo. No se necesitan cuentas o claves de API de esas plataformas.

TI debe permitir los endpoints vigentes de [Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges) y los servicios requeridos en [Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-quotas), además de los que declare el complemento desplegado. Comprobar DNS, proxy, HTTPS saliente, redirecciones, cookies y experiencias conectadas. No se necesita abrir puertos entrantes ni publicar un servicio local.

# Validación del Entorno

Realizar las comprobaciones con una cuenta equivalente a la del participante. El acceso de un administrador no demuestra que las cuentas del aula tengan las mismas capacidades.

| Comprobación | Resultado esperado |
|---|---|
| Windows y aplicaciones | Windows 11 x64; Office activado, 64 bits, con canal y build registrados |
| PowerShell | Sesión 7.4 o posterior con soporte y comandos de archivos disponibles |
| Carpetas | Raíz y tres subcarpetas presentes; creación, lectura y borrado de un archivo temporal propio |
| Edición documental | DOCX, PPTX y XLSX válidos guardados y reabiertos desde las aplicaciones |
| CSV | Importación de un archivo temporal con coma y punto decimal sin convertir números en texto |
| Finance Agent | Complemento visible, usuario autenticado y dos tablas temporales seleccionables en Financial Reconciliation |
| Copilot corporativo | Cuenta correcta, respuesta de prueba y lectura del texto o archivo aportado |
| Copilot Studio | Entorno correcto; crear, guardar, probar y publicar un agente temporal permitido |
| SharePoint | Cargar, abrir y editar un documento de prueba y guardar un archivo en InformesFinancieros |
| Conocimiento | Documento compatible recuperado por el agente con cita que abre la fuente autorizada |
| Autenticación | Configuración Microsoft habilitada; acceso del usuario validado sin credenciales de servicio compartidas |
| Continuidad | Fuentes y agente del instructor se conservan hasta completar la demostración |

Para probar conocimiento, utilizar un documento temporal con una frase de control inocua, preguntar por su contenido y abrir su cita. El estado «Listo» no basta si no devuelve el contenido esperado. No garantizar los tres a cinco minutos de indexación del material: preparar la carga con anticipación y validar su disponibilidad efectiva.

Si se acredita recorte de permisos, utilizar además una cuenta de prueba sin acceso al documento y comprobar el resultado, sin cambiar permisos de datos productivos. Imprimir «Permiso concedido» con `Write-Host` no consulta Graph ni prueba acceso delegado.

La interfaz de conciliación puede guiar la selección de tablas y claves en lugar de aceptar todos los prompts del material. Una prueba satisfactoria debe verificar el flujo real disponible. No exigir que la instalación produzca nombres de hojas, puntuaciones o columnas que solo aparecen en ejemplos de salida.

# Comandos de Verificación

## Sistema, PowerShell y despliegue Office

Ejecutar en PowerShell sobre Windows:

```powershell
$PSVersionTable | Select-Object PSVersion, PSEdition
[Environment]::Is64BitOperatingSystem
[Environment]::Is64BitProcess
Get-CimInstance Win32_OperatingSystem | Select-Object Caption, Version, OSArchitecture
Get-CimInstance Win32_ComputerSystem |
    Select-Object @{Name='RAM_GB';Expression={[math]::Round($_.TotalPhysicalMemory / 1GB, 1)}}
Get-PSDrive -Name C | Select-Object Name, Root,
    @{Name='Libre_GB';Expression={[math]::Round($_.Free / 1GB, 1)}}
Get-Command New-Item, Set-Content, Get-Content, Get-ChildItem, Select-Object

$officeConfig = 'HKLM:\SOFTWARE\Microsoft\Office\ClickToRun\Configuration'
if (Test-Path -LiteralPath $officeConfig) {
    Get-ItemProperty -LiteralPath $officeConfig |
        Select-Object VersionToReport, Platform, ProductReleaseIds, UpdateChannel
} else {
    Write-Warning 'No se encontró la configuración Click-to-Run estándar; verificar Archivo > Cuenta en Office.'
}
```

Resultados esperados: Windows 11, arquitectura de 64 bits, `True` en ambas consultas de arquitectura, comandos resueltos y versión de Office registrada con plataforma `x64`. La consulta de registro no demuestra activación ni licencia de Copilot; comprobarlas dentro de la aplicación y con TI.

## Carpetas, escritura y lectura CSV

```powershell
$labRoot = 'C:\Labs\M365_Copilot_Finance'
$paths = @(
    $labRoot,
    (Join-Path $labRoot 'Lab01_Fuentes'),
    (Join-Path $labRoot 'Lab02_Conciliacion'),
    (Join-Path $labRoot 'Lab03_Agente')
)
foreach ($path in $paths) {
    [pscustomobject]@{
        Ruta = $path
        Existe = Test-Path -LiteralPath $path -PathType Container
    }
}

$testFile = Join-Path $labRoot ('setup-' + [guid]::NewGuid().ToString() + '.csv')
try {
    @('Fecha,Importe', '2025-01-01,12.50') |
        Set-Content -LiteralPath $testFile -Encoding utf8 -ErrorAction Stop
    $row = Import-Csv -LiteralPath $testFile -Delimiter ',' -Encoding utf8 -ErrorAction Stop
    $number = [double]::Parse($row.Importe, [Globalization.CultureInfo]::InvariantCulture)
    if ($row.Fecha -ne '2025-01-01' -or $number -ne 12.5) {
        throw 'La lectura del archivo de prueba no coincide con el formato esperado.'
    }
    'SETUP_ARCHIVOS_OK'
}
finally {
    if (Test-Path -LiteralPath $testFile) {
        Remove-Item -LiteralPath $testFile -ErrorAction Stop
    }
}
```

Resultado esperado: `True` para las cuatro rutas y `SETUP_ARCHIVOS_OK`. Solo se elimina el archivo temporal recién creado. Esta comprobación no reemplaza la importación de CSV desde Excel.

Para listar fuentes cuando se hayan creado, utilizar el cmdlet correcto:

```powershell
Get-ChildItem -LiteralPath 'C:\Labs\M365_Copilot_Finance\Lab03_Agente' -File |
    Select-Object Name, Length, LastWriteTime
```

`Select-Name` aparece en varios bloques originales y no es el cmdlet correcto. Sustituirlo por `Select-Object` en las copias de trabajo.

## Conectividad

```powershell
$serviceHosts = @(
    'copilot.cloud.microsoft',
    'copilotstudio.microsoft.com',
    'login.microsoftonline.com',
    'github.com'
)
foreach ($serviceHost in $serviceHosts) {
    Resolve-DnsName -Name $serviceHost -ErrorAction Continue
    Test-NetConnection -ComputerName $serviceHost -Port 443 -InformationLevel Detailed
}
```

Resultado esperado: resolución DNS y `TcpTestSucceeded : True` cuando existe salida directa permitida. Agregar a la comprobación el host real de SharePoint comunicado por TI; no probar el dominio Contoso de ejemplo como si fuera el entorno del cliente.

Una red con proxy obligatorio puede impedir la conexión directa de este diagnóstico y permitir el navegador. Verificar la ruta institucional antes de concluir que el servicio no funciona. DNS o TCP correctos no acreditan autenticación, licencias, lectura de SharePoint ni publicación de agentes.

## Comprobaciones en las aplicaciones

Registrar Edge desde `edge://settings/help`, Office desde **Archivo > Cuenta > Acerca de Excel** y la disponibilidad de Finance Agent desde su panel en Excel. Completar la tabla de validación mediante las sesiones autenticadas.

El repositorio no tiene wrappers ni scripts capaces de certificar por consola el complemento, permisos OBO o publicación. No instalar Microsoft Graph PowerShell, PnP o un SDK solo para simular esa evidencia.

# Troubleshooting

| Síntoma | Comprobación y corrección |
|---|---|
| Finance Agent no aparece | Revisar asignación a usuario/grupo, despliegue de la aplicación oficial, propagación y sesión de Office. Confirmar la experiencia vigente con TI. |
| Excel tiene Copilot pero no Financial Reconciliation | Son capacidades distintas. Comprobar el complemento requerido; no asumir que el chat de Excel equivale a Finance Agent. |
| La pantalla no coincide con el supuesto chat de Finance Agent | Usar la ruta asistida oficial disponible y ensayar la adaptación del material antes de impartir. No prometer columnas o comandos no soportados. |
| CSV queda en una columna o importes como texto | Importar con delimitador coma, UTF-8 y tipo numérico con configuración regional adecuada. Cambiar solo el formato visual de la celda no convierte texto en número. |
| El agente no detecta los datos | Convertir el rango en tabla de Excel con encabezados y revisar nombres y tipos. |
| Copilot Studio permite pruebas pero no publicación | Comprobar licencia y derechos de publicación, roles y capacidad del entorno. Un trial no acredita el requisito de publicar. |
| SharePoint abre pero el agente no recupera las fuentes | Verificar autenticación, formato compatible, alcance de URL, procesamiento y políticas del tenant. Una fuente TXT visible en la biblioteca puede no servir en la integración elegida. |
| El documento está Listo pero no genera respuestas | Revisar cifrado, contraseña, permisos y configuración de la fuente; realizar una consulta de contenido y abrir su cita. No retirar protecciones de documentos productivos. |
| Error 401/403 | Confirmar cuenta, tenant, entorno, permisos y políticas de acceso. No cambiar a Sin autenticación ni otorgar permisos globales para continuar. |
| Cifras o texto cambian al generar fuentes con PowerShell | Revisar interpolación y escapes del here-string; usar contenido literal y comparar el archivo guardado con la fuente original. |
| `Select-Name` no se reconoce | Sustituir por `Select-Object Name, Length, LastWriteTime`. |
| Acceso denegado en `C:\Labs` | TI debe preparar la carpeta y conceder escritura al participante, o acordar una raíz alternativa y actualizar todas las rutas. |
| El agente o los documentos desaparecen antes de la demostración | Posponer la limpieza destructiva hasta terminar las actividades que reutilizan esos recursos. |
| No se produce un reporte automático en una fecha | Los pasos implementan una ejecución manual. Guardar un prompt no crea programación; se necesita una ruta adicional validada si se exige recurrencia real. |

# Checklist Final

- [ ] Windows 11 de 64 bits y recursos suficientes para Office y navegador.
- [ ] Excel, Word y PowerPoint activados; versión, build, canal y arquitectura registrados.
- [ ] PowerShell común instalado y comandos locales disponibles.
- [ ] Cuenta nativa del tenant asignado y derechos de Microsoft 365 Copilot confirmados.
- [ ] Finance Agent oficial asignado y conciliación asistida comprobada en Excel.
- [ ] Entorno Copilot Studio/Dataverse habilitado con autoría, capacidad y publicación verificadas.
- [ ] Sitio, biblioteca y permisos SharePoint reales comunicados al grupo.
- [ ] Carpeta InformesFinancieros y separación de fuentes preparadas.
- [ ] Raíz local y tres subcarpetas con escritura comprobada.
- [ ] Formatos DOCX/PDF de conocimiento acordados y referencias de las copias de trabajo alineadas.
- [ ] UTF-8, importación CSV, decimales, fechas y tablas de Excel probados.
- [ ] URL y usuarios Contoso sustituidos por los del laboratorio.
- [ ] Fuentes de conocimiento recuperadas con citas mediante autenticación Microsoft.
- [ ] Correcciones de PowerShell y conservación de recursos aplicadas a las copias de trabajo.
- [ ] Ejecución manual y eventual programación real claramente diferenciadas.
- [ ] Registro de validación completado sin contraseñas ni tokens.

# Resumen

El entorno general utiliza Windows 11, Microsoft 365 Apps de 64 bits, Copilot corporativo, Finance Agent para Excel y Copilot Studio con Dataverse y SharePoint. Los archivos financieros se generan localmente; no se necesitan conexiones a ERP ni a proveedores externos de información financiera.

La aprobación del setup exige pruebas reales de Finance Agent, publicación y recuperación de documentos con la cuenta del participante. La simple presencia de licencias, carpetas o vínculos no acredita esas capacidades.

## Correcciones de versiones y alcance aplicadas

| Hallazgo | Criterio de preparación |
|---|---|
| Office 2408, build 17928.20156, se presenta también como versión de Copilot | Separar cliente Office de servicio SaaS; usar Office soportado y registrar la experiencia de Copilot. |
| Copilot Studio v2024.11.1 y Power Automate build 2409.2 se presentan como versiones fijables | No buscar instaladores con esos números; los servicios se administran por Microsoft. |
| Finance Agent v1.0.2409.1 | Desplegar el complemento oficial vigente y validar su funcionalidad, sin asumir distribución de ese build. |
| E5 se exige como único contexto | Validar derechos efectivos de aplicaciones, Copilot y Finance Agent; E5 no sustituye el despliegue del complemento. |
| PowerShell 5.1, 7.4.x y 7.4.5 alternan | Usar una sesión 7.x soportada, mínimo 7.4, y registrar su parche. |
| Entra ID «v2.0» se lista como software | No instalar Entra ID localmente; es el servicio de identidad y la versión de protocolo no es una versión del tenant. |
| TXT generado frente a DOCX/PDF declarado | Preparar documentos reales compatibles con la ruta de conocimiento SharePoint. |
| La limpieza elimina recursos que se reutilizan | Conservarlos hasta el cierre final autorizado. |
| Scripts imprimen resultados de permisos sin consultar el servicio | Validar mediante sesión autenticada y prueba funcional; no aceptar mensajes impresos como evidencia. |
| SETUP_GUIDE.md enlaza `Netec-Mx/261103-M365-AGENT-FINAN-LD` | Utilizar el repositorio real `Netec-Mx/M365_AGENT_FINAN_LD_Priv`. |

## Alcance de la validación documental

Se revisó el contenido completo de los tres capítulos y cinco actividades del commit indicado, además de los archivos generales e inventario de recursos. Se contrastaron los requisitos de Office, Finance Agent, Copilot Studio y SharePoint con documentación oficial.

No se tuvo acceso a Windows, Office ni al tenant del cliente. Los comandos PowerShell, las licencias, el complemento, las fuentes y la publicación deben validarse en las estaciones y cuentas reales antes de impartir. No se afirma haber ejecutado los laboratorios ni comprobado sus resultados financieros. La rutina programada no queda acreditada porque el repositorio no implementa su configuración.

## Referencias oficiales

- [Repositorio en la revisión analizada](https://github.com/Netec-Mx/M365_AGENT_FINAN_LD_Priv/tree/b2e92a12971313e16a9d66e79503201e95a22132).
- [Requisitos de Microsoft 365 para uso empresarial](https://support.microsoft.com/en-us/office/system-requirements/system-requirements-for-microsoft-365-for-business-education-and-government-use).
- [Versiones soportadas de Microsoft 365 Apps](https://learn.microsoft.com/en-us/officeupdates/update-history-microsoft365-apps-by-date).
- [Requisitos de Microsoft Copilot](https://learn.microsoft.com/en-us/copilot/plan/microsoft-copilot-requirements).
- [Instalación de PowerShell en Windows](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows).
- [Despliegue de Finance Agent](https://learn.microsoft.com/en-us/copilot/finance/get-started/deployment-guide).
- [Finance Agent: despliegue administrativo del complemento](https://learn.microsoft.com/en-us/copilot/finance/get-started/install-admin-deployed).
- [Finance Agent: instalación individual autorizada](https://learn.microsoft.com/en-us/copilot/finance/get-started/install-user-deployed).
- [Conciliación asistida en Excel](https://learn.microsoft.com/en-us/copilot/finance/reconcile/reconcile-data).
- [Acceso y limitaciones del trial de Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-licensing-subscriptions).
- [Licencias y acceso de autores](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-licensing).
- [Entornos de Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/environments-first-run-experience).
- [SharePoint como conocimiento](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-sharepoint).
- [Formatos, límites y servicios requeridos](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-quotas).
