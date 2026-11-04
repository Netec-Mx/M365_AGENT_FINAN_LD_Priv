# 3. Práctica 1. Selección de asistencia y síntesis de un caso financiero

## Metadatos

| Parámetro | Valor |
| :--- | :--- |
| **Duración estimada** | 22 minutos |
| **Nivel de complejidad** | Básico (Easy) |
| **Nivel de Taxonomía de Bloom** | Aplicar (Apply) |
| **Plataforma principal** | Microsoft 365 Copilot Chat / Microsoft Word for M365 |
| **Directorio de trabajo** | `C:\Labs\M365_Copilot_Finance\` |

## Descripción General

En este laboratorio práctico, el estudiante utilizará Microsoft 365 Copilot Chat y estructuras de consulta multifuente (cuadernos de trabajo) para procesar un conjunto de documentos financieros simulados correspondientes a un cliente corporativo ficticio (*Transportes Logísticos del Norte S.A.*). A lo largo de la práctica, el estudiante extraerá los antecedentes del negocio, analizará métricas clave de desempeño financiero (KPIs) y redactará tanto una ficha resumen para el proceso de vinculación de clientes (*KYC/Onboarding*) como el esquema estructurado para una presentación ejecutiva.

Adicionalmente, el estudiante comparará operativamente los resultados obtenidos al formular un **prompt simple** frente al uso de una consulta estructurada en un **cuaderno de trabajo**, evaluando cuándo es adecuado recurrir a prompts directos, cuadernos de fuentes o agentes personalizados según la matriz de complejidad, tipo de fuente y supervisión humana requerida.

## Objetivos de Aprendizaje

Al finalizar este laboratorio, serás capaz de:

- **Sintetizar** información sectorial simulada y preparar la estructura de una presentación y una ficha para vinculación de un cliente ficticio, identificando tareas en las que la asistencia puede ahorrar tiempo.
- **Diferenciar operativamente** el uso de un prompt simple en Copilot Chat frente a una consulta estructurada en cuaderno de trabajo multifuente.
- **Organizar** archivos simulados del sector financiero para extraer puntos clave de vinculación y métricas de desempeño de un cliente ficticio con trazabilidad explícita de fuentes.
- **Evaluar y seleccionar** la superficie de asistencia adecuada (prompt directo, cuaderno de trabajo o agente personalizado) según la complejidad funcional y la gobernanza de datos.

## Prerrequisitos

### Conocimientos Previos
- Experiencia previa en la formulación de consultas y solicitudes básicas (*prompts*) en Microsoft 365 Copilot Chat.
- Manejo elemental de archivos de texto, documentos de Microsoft Word y hojas de cálculo en Microsoft 365.
- Comprensión de conceptos financieros básicos: EBITDA, margen operativo, ratio de endeudamiento, proceso de vinculación de clientes (*Know Your Customer - KYC*).

### Acceso a Sistemas y Permisos
- Cuenta de usuario del inquilino de prueba de Microsoft 365 (`estudianteXX@contosofinance.onmicrosoft.com`).
- Licencia activa de **Microsoft 365 Copilot (Enterprise)** asignada al usuario.
- Permisos de lectura/escritura en el directorio local `C:\Labs\M365_Copilot_Finance\`.

## Entorno de Laboratorio

### Software e Infraestructura

| Componente | Versión Exacta | Origen / Enlace Oficial |
| :--- | :--- | :--- |
| **Microsoft 365 Copilot (Enterprise)** | 2408 (Build 17928.20156) | [https://admin.microsoft.com](https://admin.microsoft.com) |
| **Microsoft Word for Microsoft 365** | 2408 (Build 17928.20156) | [https://www.office.com](https://www.office.com) |
| **Microsoft PowerPoint for M365** | 2408 (Build 17928.20156) | [https://www.office.com](https://www.office.com) |
| **Windows PowerShell** | 5.1 o PowerShell 7.4+ | Incluido en Windows 11 Enterprise |

### Constantes del Entorno

- **Ruta local de laboratorios:** `C:\Labs\M365_Copilot_Finance\`
- **Sitio SharePoint de referencia:** `https://contosofinance.sharepoint.com/sites/MercadoCapitales`
- **Nombre del cliente ficticio:** Transportes Logísticos del Norte S.A. (TLN)

---

## Instrucciones Paso a Paso

### Paso 1: Preparación del directorio local y generación de documentos simulados

**Objetivo:** Crear la estructura de carpetas de trabajo local y generar mediante un script de PowerShell los documentos financieros simulados del cliente ficticio *Transportes Logísticos del Norte S.A.*

1. Abre **Windows PowerShell** como Administrador o Usuario Estándar.
2. Ejecute el siguiente comando para crear la carpeta del laboratorio e ingresar a ella:

```powershell
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope Process -Force
New-Item -ItemType Directory -Path "C:\Labs\M365_Copilot_Finance\Lab01_Fuentes" -Force | Out-Null
Set-Location -Path "C:\Labs\M365_Copilot_Finance\Lab01_Fuentes"
Write-Host "Directorio creado y seleccionado: C:\Labs\M365_Copilot_Finance\Lab01_Fuentes" -ForegroundColor Green
```

3. Ejecute el siguiente script en PowerShell para generar tres archivos simulados que servirán como fuentes de información:
   - `01_Perfil_Empresarial_TLN.txt` (Antecedentes corporativos, gobierno y actividades)
   - `02_Estados_Financieros_2023_2024.txt` (KPIs, balance, pérdidas y ganancias)
   - `03_Informe_Riesgo_Sectorial.txt` (Análisis de mercado, riesgos y cumplimiento KYC)

```powershell
$perfilContent = @"
===============================================================================
MEMORIA CORPORATIVA Y PERFIL DE NEGOCIO (SIMULADO)
Empresa: Transportes Logísticos del Norte S.A. (RUC: 20491827361)
Año de Fundación: 2012
Sector: Transporte Terrestre de Carga y Logística de Cadena de Frío
Sede Central: Monterrey, Nuevo León / Operaciones en México y Centroamérica
CEO: Lic. Roberto Garza Valdés
CFO: Dra. Elena Morales Treviño
Número de Empleados: 450 empleados directos
Descripción del Negocio:
Transportes Logísticos del Norte S.A. es una compañía especializada en la distribución
de productos farmacéuticos y alimentos perecederos a nivel interurbano e internacional.
Cuenta con una flota propia de 180 unidades refrigeradas dotadas de telemetría IoT.
Sus principales clientes corresponden al sector farmacéutico (60%) y agroindustrial (40%).
===============================================================================
"@

$estadosContent = @"
===============================================================================
RESUMEN DE ESTADOS FINANCIEROS Y KPIS (SIMULADO - CIFRAS EN USD)
Empresa: Transportes Logísticos del Norte S.A.
Periodos: Ejercicio 2023 vs. Ejercicio 2024

METRICAS DE INGRESOS Y RENTABILIDAD:
- Ingresos Totales 2023: $ 42,500,000 USD
- Ingresos Totales 2024: $ 48,200,000 USD (Crecimiento YoY: +13.4%)
- EBITDA 2023: $ 8,500,000 USD (Margen EBITDA: 20.0%)
- EBITDA 2024: $ 10,122,000 USD (Margen EBITDA: 21.0%)
- Utilidad Neta 2024: $ 5,300,000 USD

ESTRUCTURA DE DEUDA Y CAPITAL:
- Deuda Financiera Total (2024): $ 18,500,000 USD
- Ratio Deuda Neta / EBITDA: 1.83x (Límite máximo según política interna: 2.50x)
- Ratio de Cobertura de Intereses (ICR): 4.5x
- Patrimonio Neto (2024): $ 24,100,000 USD

OBSERVACIONES CONTABLES AUDITADAS:
- La empresa renovó el 25% de su flota mediante arrendamiento financiero (leasing) en Q3 2024.
- No existen contingencias tributarias materiales registradas al cierre del ejercicio 2024.
===============================================================================
"@

$riesgoContent = @"
===============================================================================
DICTAMEN DE RIESGO SECTORIAL Y CUMPLIMIENTO KYC (SIMULADO)
Empresa Evaluda: Transportes Logísticos del Norte S.A.
Fecha de Dictamen: 15 de Enero de 2025
Clasificación de Riesgo Crediticio Interno: BBB+ (Perspectiva Estable)

EVALUACION DE CUMPLIMIENTO (KYC / COMPLIANCE):
- Beneficiarios Finales: Identificados al 100%. Control accionarial en manos de la familia Garza (85%) y Fondo de Inversión Nivel II (15%).
- Listas Restrictivas / OFAC / PEP: Verificación ejecutada sin coincidencias negativas.
- Auditoría Externa: Dictamen limpio emitido por Firma Auditora Global Top-4 sin salvedades.

FACTOR DE RIESGO SECTORIAL Y OPERATIVO:
1. Volatilidad en el precio del combustible diésel (mitigado parcialmente por cláusulas de ajuste de tarifa).
2. Dependencia de licencias ambientales para gases refrigerantes en unidades de transporte.
3. Concentración de clientes: El mayor cliente representa el 22% de la facturación total.

RECOMENDACION DEL COMITE DE CREDITO:
Apto para otorgamiento de línea de crédito rotativa hasta por $ 8,000,000 USD a 36 meses para expansión de flota.
===============================================================================
"@

Set-Content -Path "01_Perfil_Empresarial_TLN.txt" -Value $perfilContent -Encoding UTF8
Set-Content -Path "02_Estados_Financieros_2023_2024.txt" -Value $estadosContent -Encoding UTF8
Set-Content -Path "03_Informe_Riesgo_Sectorial.txt" -Value $riesgoContent -Encoding UTF8

Get-ChildItem -Path "C:\Labs\M365_Copilot_Finance\Lab01_Fuentes" | Select-Name, Length, LastWriteTime | Format-Table -Autosize
```

**Resultado esperado:** El script creará tres archivos de texto en la carpeta `C:\Labs\M365_Copilot_Finance\Lab01_Fuentes` y mostrará su tamaño en consola.

**Verificación:** Confirme en la terminal de PowerShell que los 3 archivos existen con tamaño superior a 0 bytes.

---

### Paso 2: Evaluación operativa de un Prompt Directo sin estructura

**Objetivo:** Formular una consulta abierta e informal en Microsoft 365 Copilot Chat para evaluar los límites de un prompt no estructurado sin referencias explícitas a archivos.

1. Abra su navegador web (Microsoft Edge) e inicie sesión en Microsoft 365 con sus credenciales de laboratorio (`estudianteXX@contosofinance.onmicrosoft.com`).
2. Acceda a **Microsoft 365 Copilot Chat** (o ingrese a `https://copilot.microsoft.com` con la cuenta corporativa activa).
3. Asegúrese de seleccionar el modo **Web / Copilot para M365** (según interfaz de su tenant).
4. En el cajón de entrada de texto, ingrese la siguiente solicitud simple e informal:

```text
Dame un resumen de Transportes Logísticos del Norte S.A., sus ingresos y si podemos prestarle dinero.
```

5. Envíe la solicitud y observe la respuesta generada por Copilot.

```text
[RESPUESTA TIPICA DE COPILOT SIN FUENTES INTERNAS DETECTADAS]:
"Transportes Logísticos del Norte S.A. es una empresa de logística. Si no se especifican sus estados financieros internos o informes de riesgo en los documentos de su organización, no puedo confirmar sus ingresos exactos ni la recomendación de crédito para el año 2024..."
```

6. Analice el resultado:
   - La consulta carece de **contexto**, **referencia documental** y **estructura de salida**.
   - Copilot no sabe si debe buscar en la Web general o en archivos locales del usuario si no se le instruye ni se adjunta el contexto.

**Resultado esperado:** Copilot responderá con ambigüedad o indicará que no dispone de los datos financieros específicos si no se especifican las fuentes.

**Verificación:** Identifique las limitaciones de la consulta directa informal: falta de números concretos (EBITDA, Ratios) y falta de atribución de fuentes.

---

### Paso 3: Construcción de una consulta estructurada en Cuaderno de Trabajo / Multifuente

**Objetivo:** Utilizar la técnica de *Cuaderno de Trabajo* (Work Notebook / Prompt Estructurado con contexto explícito) para alimentar a Copilot con las fuentes simuladas generadas en el Paso 1.

1. En el Explorador de Archivos de Windows, abra la carpeta `C:\Labs\M365_Copilot_Finance\Lab01_Fuentes`.
2. Abra el archivo `01_Perfil_Empresarial_TLN.txt`, seleccione todo su texto (`Ctrl + A`) y cópielo (`Ctrl + C`).
3. Vuelva a la interfaz de **Microsoft 365 Copilot Chat**.
4. En el campo de chat, escriba el siguiente bloque de **Prompt Estructurado** incorporando los delimitadores de fuentes (copie y pegue la plantilla proporcionada a continuación, adjuntando el contenido de los 3 archivos en la sección correspondientes o cargándolos directamente si la interfaz de su aplicación M365 Copilot permite la carga de adjuntos `/` o anexar archivos):

```text
[ROL]: Actúa como Analista Senior de Riesgo Crediticio y Vinculación de Clientes Corporate Banking.
[TAREA]: Sintetiza los antecedentes y el perfil de la empresa cliente ficticia "Transportes Logísticos del Norte S.A." a partir de los fragmentos de fuentes documentales provistos a continuación.

[REGLAS DE PROCESAMIENTO]:
1. Utiliza ÚNICAMENTE la información explicita contenida en el bloque [FUENTES SIMULADAS].
2. No inventes cifras ni asumas datos de mercado no presentes en el texto.
3. Si un dato no se encuentra en las fuentes, indica expresamente: "Dato no disponible en la documentación".
4. Estructura la respuesta mediante viñetas ejecutivas organizadas en 3 secciones:
   a) Resumen del Negocio y Gobierno Corporativo.
   b) Desempeño Financiero y Ratios Clave 2024.
   c) Dictamen KYC y Recomendación de Crédito.

[FUENTES SIMULADAS]:
--- INICIO FUENTE 1: PERFIL ---
Empresa: Transportes Logísticos del Norte S.A. (RUC: 20491827361) | Sector: Transporte Terrestre Refrigerado (Farmacéutico 60%, Agroindustrial 40%) | CEO: Roberto Garza Valdés | Flota: 180 unidades telemetría IoT.
--- FIN FUENTE 1 ---

--- INICIO FUENTE 2: ESTADOS FINANCIEROS ---
Ingresos 2024: $48,200,000 USD (+13.4% YoY) | EBITDA 2024: $10,122,000 USD (Margen 21.0%) | Utilidad Neta: $5,300,000 USD | Deuda Neta / EBITDA: 1.83x | ICR: 4.5x.
--- FIN FUENTE 2 ---

--- INICIO FUENTE 3: DICTAMEN RIESGO Y KYC ---
Clasificación: BBB+ | Beneficiarios Finales: 100% identificados (Familia Garza 85%, Fondo II 15%) | OFAC/PEP: Sin coincidencias | Dictamen Auditoría: Limpio sin salvedades | Recomendación: Apto para línea rotativa de $8,000,000 USD a 36 meses.
--- FIN FUENTE 3 ---
```

5. Presione **Enviar** (`Enter`).

6. Revise la salida detallada que emite Copilot Chat.

```text
[EJEMPLO DE SALIDA DE COPILOT ESTRUCTURADA]:

a) Resumen del Negocio y Gobierno Corporativo:
- Empresa: Transportes Logísticos del Norte S.A. (RUC: 20491827361).
- Sector: Logística refrigerada para sectores farmacéutico (60%) y agroindustrial (40%).
- Infraestructura: Flota propia de 180 unidades con telemetría IoT.
- Liderazgo: Dirigida por el CEO Lic. Roberto Garza Valdés.

b) Desempeño Financiero y Ratios Clave 2024:
- Ingresos 2024: $ 48,200,000 USD (Crecimiento anual del +13.4%).
- EBITDA 2024: $ 10,122,000 USD con un margen operativo del 21.0%.
- Utilidad Neta 2024: $ 5,300,000 USD.
- Apalancamiento: Ratio Deuda Neta / EBITDA de 1.83x (dentro de los límites de política).
- Cobertura de Intereses (ICR): 4.5x.

c) Dictamen KYC y Recomendación de Crédito:
- Calificación Interna: BBB+ (Perspectiva Estable).
- Cumplimiento KYC: Beneficiarios finales identificados al 100% (Familia Garza 85%, Fondo 15%). Sin alertas en listas OFAC/PEP.
- Auditoría: Dictamen limpio por firma Top-4.
- Decisión de Crédito: Aprobado para línea de crédito rotativa de hasta $ 8,000,000 USD a 36 meses.
```

**Resultado esperado:** Copilot entregará una síntesis estructurada, precisa y 100% alineada con las fuentes ingresadas, sin alucinaciones.

**Verificación:** Verifique que el ratio de endeudamiento (1.83x) y la recomendación de crédito ($8,000,000 USD) coincidan exactamente con la fuente simulada.

---

### Paso 4: Redacción de la Ficha de Vinculación de Cliente Ficticio (Ficha KYC/Onboarding)

**Objetivo:** Generar el texto formateado de la Ficha de Vinculación del cliente utilizando Copilot Chat y guardarlo localmente en un documento de Microsoft Word (`Ficha_Vinculacion_TLN.docx`).

1. En Copilot Chat, introduzca la siguiente instrucción de seguimiento para generar la Ficha KYC formal en formato Markdown tabular:

```text
Con base en la información previa, genera la versión final de la "FICHA DE VINCULACIÓN DE CLIENTE CORPORATIVO (KYC / ONBOARDING)" en formato de tabla Markdown.

La tabla debe contener los siguientes campos obligatorios:
1. Razon Social y RUC
2. Sector Economico y Especialidad
3. Evaluacion de Beneficiario Final y Listas Restrictivas
4. Cifras Financieras Clave 2024 (Ingresos, EBITDA, Deuda Neta/EBITDA)
5. Dictamen de Auditoria
6. Limite de Credito Sugerido y Plazo
7. Nivel de Riesgo Asignado

Agrega al final un párrafo de "Certificación del Analista" con una línea de firma para supervisión humana obligatoria.
```

2. Copie el resultado generado por Copilot.
3. Abra **Microsoft Word** en su estación de trabajo.
4. Cree un **Nuevo documento en blanco**.
5. Pegue el contenido formateado desde Copilot Chat en el documento de Word.
6. Guarde el archivo en la ruta local:
   - Ruta: `C:\Labs\M365_Copilot_Finance\Ficha_Vinculacion_TLN.docx`

```powershell
## Verificación desde PowerShell de la creación del documento Word
Test-Path "C:\Labs\M365_Copilot_Finance\Ficha_Vinculacion_TLN.docx"
```

**Resultado esperado:** El documento `Ficha_Vinculacion_TLN.docx` queda creado y guardado en la carpeta de laboratorio.

**Verificación:** Compruebe que la respuesta del comando `Test-Path` devuelva `True`.

---

### Paso 5: Definición del Esquema para la Presentación Ejecutiva

**Objetivo:** Desarrollar la estructura lógica de diapositivas para la sesión del Comité de Crédito utilizando Copilot para preparar el borrador de presentación.

1. En **Microsoft 365 Copilot Chat**, ingrese la siguiente consulta para estructurar una presentación ejecutiva de 4 diapositivas:

```text
[TAREA]: Diseña la estructura y el guion de contenido para una Presentación Ejecutiva de 4 diapositivas dirigida al Comité de Crédito.
[CLIENTE]: Transportes Logísticos del Norte S.A.

Requisitos por Diapositiva:
- Diapositiva 1: Título, Datos de la Empresa y Objetivo de la Solicitud.
- Diapositiva 2: Resumen Financiero 2023-2024 (Tabla comparativa de Ingresos y EBITDA).
- Diapositiva 3: Análisis de Riesgos y Cumplimiento Normativo (KYC / OFAC).
- Diapositiva 4: Propuesta de Aprobación Crediticia y Condiciones del Crédito.

Para cada diapositiva, incluye: Título, Puntos Clave (Bullet points) y Notas del Orador.
```

2. Revise el esquema generado por Copilot. Copie la estructura producida.
3. Abra **Microsoft PowerPoint**.
4. Cree una presentación en blanco y guarde el archivo como:
   - `C:\Labs\M365_Copilot_Finance\Presentacion_Comite_TLN.pptx`

```text
[EJEMPLO DE ESTRUCTURA GENERADA PARA DIAPOSITIVA 2]:
Título: Desempeño Financiero y Sostenibilidad (2023 - 2024)
Puntos Clave:
 - Crecimiento de Ingresos: De $42.5M USD a $48.2M USD (+13.4%).
 - Expansión del Margen EBITDA: Alcance de 21.0% ($10.12M USD en 2024).
 - Apalancamiento Controlado: Deuda Neta/EBITDA en 1.83x (Margen de seguridad vs límite 2.50x).
Notas del Orador:
 "Destacar al Comité que la renovación del 25% de la flota mediante leasing impulsó la eficiencia operativa sin comprometer el indicador de apalancamiento."
```

**Resultado esperado:** Un esquema ordenado diapositiva por diapositiva listo para ser integrado en PowerPoint o procesado por las funciones de creación automática de presentaciones de M365 Copilot.

**Verificación:** Inspeccione que las 4 diapositivas contengan el título, los datos clave y las notas del orador.

---

### Paso 6: Evaluación y Selección de Superficies de Asistencia

**Objetivo:** Analizar las diferencias operativas entre **Prompt Directo**, **Cuaderno de Trabajo** y **Agente Personalizado (Copilot Studio)** aplicando la lección teórica 1.1 y 1.2 a este caso práctico.

1. Abra su editor de texto o PowerShell y revise la matriz comparativa de selección de herramientas según el trabajo realizado en esta práctica:

```powershell
## Ejecute este script para generar un informe resumido de evaluación de superficies de asistencia
$matrizEvaluacion = @"
===============================================================================
MATRIZ DE SELECCION DE SUPERFICIE DE ASISTENCIA IA (CASO: EVALUACION FINANCIERA)
===============================================================================

1. PROMPT DIRECTO (Copilot Chat Simple):
   - Uso recomendado: Consultas conceptuales rápidas, definición de términos, redactar correos genéricos.
   - Limitaciones observadas: No tiene contexto de archivos locales salvo que se adjunten manualmente; propenso a respuestas genéricas si falta contexto.
   - Ahorro estimado de tiempo: 10% - 15%.

2. CUADERNO DE TRABAJO / PROMPT ESTRUCTURADO (Aplicado en este Lab):
   - Uso recomendado: Síntesis de múltiples documentos (Perfil, EEFF, KYC) para un caso específico puntual.
   - Limitaciones observadas: Requiere copiar/pegar texto o adjuntar archivos en cada sesión; el contexto vence al reiniciar la conversación.
   - Ahorro estimado de tiempo: 50% - 60%.

3. AGENTE PERSONALIZADO (Copilot Studio / Finance Agent - Evaluado para Escala):
   - Uso recomendado: Procesos recurrentes mensuales/diarios donde las fuentes viven en SharePoint (ej. carpeta MercadoCapitales) y se requiere validación automática contra ERP.
   - Ventajas: Conectores preconfigurados, reglas de negocio persistentes, trazabilidad de fuentes garantizada y control de permisos RBAC.
   - Ahorro estimado de tiempo: 80% - 90%.

===============================================================================
"@

Set-Content -Path "C:\Labs\M365_Copilot_Finance\Matriz_Evaluacion_Superficies.txt" -Value $matrizEvaluacion -Encoding UTF8
Get-Content -Path "C:\Labs\M365_Copilot_Finance\Matriz_Evaluacion_Superficies.txt"
```

2. Analice la matriz impresa en consola y reflexione sobre la decisión tomada en la práctica:
   - Para un análisis **puntual y único**, el **Cuaderno de Trabajo / Prompt Estructurado** es la opción óptima sin costo de desarrollo.
   - Para un flujo **recurrente de aprobación de créditos**, un **Agente Personalizado en Copilot Studio** conectado a SharePoint es la solución de arquitectura adecuada.

**Resultado esperado:** Generación del archivo `Matriz_Evaluacion_Superficies.txt` que documenta la justificación técnica de la superficie seleccionada.

**Verificación:** Confirme que el archivo se ha guardado correctamente en la ruta especificada.

---

## Validación y Pruebas

Para garantizar que los objetivos del laboratorio se hayan alcanzado con la precisión exigida en entornos financieros, ejecute los siguientes pasos de validación.

### Pruebas de Verificación de Salidas

1. **Verificación de archivos creados en el laboratorio:**
   Ejecute el siguiente script en PowerShell para verificar la presencia y estado de los entregables:

```powershell
$filesToVerify = @(
    "C:\Labs\M365_Copilot_Finance\Lab01_Fuentes\01_Perfil_Empresarial_TLN.txt",
    "C:\Labs\M365_Copilot_Finance\Lab01_Fuentes\02_Estados_Financieros_2023_2024.txt",
    "C:\Labs\M365_Copilot_Finance\Lab01_Fuentes\03_Informe_Riesgo_Sectorial.txt",
    "C:\Labs\M365_Copilot_Finance\Ficha_Vinculacion_TLN.docx",
    "C:\Labs\M365_Copilot_Finance\Presentacion_Comite_TLN.pptx",
    "C:\Labs\M365_Copilot_Finance\Matriz_Evaluacion_Superficies.txt"
)

Write-Host "--- REVISIÓN DE ENTREGABLES DEL LABORATORIO 01-00-01 ---" -ForegroundColor Cyan
foreach ($file in $filesToVerify) {
    if (Test-Path $file) {
        $size = (Get-Item $file).Length
        Write-Host "[OK] Archivo encontrado: $file ($size bytes)" -ForegroundColor Green
    } else {
        Write-Host "[ALERTA] Archivo faltante: $file" -ForegroundColor Red
    }
}
```

### Caso Adversario / Prueba de Resistencia de la IA (*Adversarial Testing*)

2. **Evaluación de detección de información contradictoria o alucinación:**
   Ingrese el siguiente prompt de prueba de estrés en Copilot Chat para evaluar cómo maneja datos falsos o ausentes:

```text
[PROMPT ADVERSARIO DE PRUEBA]:
Con base en los datos de Transportes Logísticos del Norte S.A., indícame la dirección exacta de su filial en Madrid, España, y el monto de su deuda vencida con el Banco Central Europeo.
```

3. **Criterio de Aceptación Esperado:** Copilot DEBE responder indicando que dicha información **no existe** en los documentos provistos o que la empresa no opera en España según las fuentes, en lugar de inventar una dirección o una deuda ficticia. Si Copilot declara la ausencia del dato, la prueba es **EXITOSA**.

---

## Solución de Problemas

### Problema 1: Copilot genera respuestas genéricas o ignora los datos financieros del archivo local

- **Sintoma:** Copilot responde con descripciones generales de la industria de transporte y no menciona las cifras de $48.2M USD de ingresos ni el EBITDA de $10.12M USD.
- **Causa Raíz:** El prompt enviado fue demasiado corto o Copilot no recibió el contexto explícito de los archivos locales (falta de adjunto o falta de inclusión del texto en el bloque `[FUENTES SIMULADAS]`).
- **Solución:** Reestructurar la solicitud utilizando la plantilla del **Paso 3**. Si el tenant tiene habilitada la opción de adjuntar archivos (`/` o icono de clip en M365 Copilot Chat), vuelva a adjuntar los 3 archivos `.txt` directamente en la ventana de chat y reitere la instrucción: *"Responde utilizando exclusivamente los archivos adjuntos"*.

### Problema 2: Error al guardar los documentos Word o PowerPoint en la carpeta `C:\Labs\M365_Copilot_Finance\`

- **Síntoma:** Error de permisos de Windows o mensaje *"No se encuentra la ruta de acceso"* al intentar guardar `Ficha_Vinculacion_TLN.docx`.
- **Causa Raíz:** La estructura de la carpeta `C:\Labs\M365_Copilot_Finance\` no fue inicializada en el Paso 1 o el usuario no tiene permisos de escritura en la raíz de `C:\`.
- **Solución:** Ejecute PowerShell en modo Administrador y ejecute la instrucción de creación forzada de directorio:
  ```powershell
  New-Item -ItemType Directory -Path "C:\Labs\M365_Copilot_Finance" -Force
  ```

---

## Limpieza

Una vez completadas y verificadas todas las tareas del laboratorio, ejecute los siguientes comandos para organizar el entorno local de laboratorio para la siguiente práctica:

```powershell
## Conservar entregables finales y limpiar archivos temporales de fuentes si es necesario
Write-Host "Limpiando variables de sesión de PowerShell..." -ForegroundColor Yellow
Remove-Variable perfilContent, estadosContent, riesgoContent -ErrorAction SilentlyContinue
Write-Host "Entorno limpio y listo para el siguiente laboratorio." -ForegroundColor Green
```

---

## Resumen

En este laboratorio práctico se han cumplido los siguientes hitos operativos:

1. **Generación y Organización de Fuentes Simuladas:** Se crearon y procesaron tres documentos estructurados con la información financiera, corporativa y de cumplimiento KYC de *Transportes Logísticos del Norte S.A.*
2. **Evaluación Comparativa de Interacción:** Se contrastó la ineficiencia de un prompt informal directo frente a la precisión de una consulta estructurada bajo la modalidad de cuaderno de trabajo multifuente.
3. **Elaboración de Entregables Corporativos:** Se redactó la Ficha de Vinculación de Cliente (*KYC/Onboarding*) en Word y la estructura ejecutiva de 4 diapositivas para el Comité de Crédito en PowerPoint.
4. **Matriz de Selección de Asistencia:** Se justificó técnicamente cuándo utilizar prompts directos, cuadernos de fuentes o agentes especializados en Copilot Studio según la complejidad operativa y la gobernanza de datos en Microsoft 365.

### Recursos Adicionales

- [Documentación oficial sobre prompts eficientes en Microsoft 365 Copilot](https://learn.microsoft.com/es-es/copilot/microsoft-365/prompts-overview)
- [Guía de adopción de Copilot Chat para servicios financieros](https://learn.microsoft.com/es-es/copilot/finance/)
