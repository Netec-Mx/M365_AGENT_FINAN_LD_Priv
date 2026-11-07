# Fuentes públicas para el conector Enterprise Websites — Práctica 4

## Propósito y delimitación

**Utilizar exactamente una conexión administrada y validada antes del curso.** El objetivo es demostrar que el agente de Microsoft 365 Copilot usa páginas **indexadas por un Microsoft 365 Copilot Connector**. Los sitios siguientes son **candidatos**, no conexiones funcionales comprobadas. No deben confundirse con los documentos internos de TLN ni utilizarse para afirmar hechos de la empresa ficticia.

| Prioridad de validación | Sitio candidato | Dirección raíz propuesta | Enfoque | Riesgo de configuración |
|---|---|---|---|---|
| 1 | Banco Mundial | https://www.worldbank.org/ | Contexto macroeconómico, desarrollo, financiación | Redirecciones internas, contenido no indexable o alcance insuficiente |
| 2 | Banco Interamericano de Desarrollo (BID) | https://www.iadb.org/ | Financiamiento y desarrollo regional | Índice sin páginas pertinentes, redirecciones o limitaciones del rastreador |
| 3 | Investopedia | https://www.investopedia.com/ | Conceptos de bonos, cupón y riesgos | Contenido dinámico, publicidad y restricciones de rastreo |

**Regla de selección:** Administrar e indexar el sitio elegido y luego abrir el agente de prueba en Agent Builder. Usar el sitio **solo si la conexión aparece y una consulta devuelve al menos una cita que se pueda abrir**. Si la conexión falla, realizar pruebas con el siguiente candidato **antes de la clase**, no durante los cinco minutos de la práctica.

## Pregunta para el Banco Mundial — si quedó indexado

```text
Usa exclusivamente la conexión empresarial FinanzasWebCurso que contiene
páginas indexadas del Banco Mundial. Explica dos temas públicos de
perspectivas económicas o desarrollo encontrados en el origen.
Para cada tema, cita el título y la URL de la página y formula una
pregunta general que un analista financiero debería investigar antes de
evaluar una emisión de bonos como la propuesta ficticia de TLN.
No atribuyas cifras del Banco Mundial a TLN, no inventes estadísticas
y no uses Búsqueda en la web como sustituto. Si el conector no devuelve
contenido verificable, indícalo explícitamente.
```

## Pregunta para el BID — si quedó indexado

```text
Usa exclusivamente la conexión empresarial FinanzasWebCurso que contiene
páginas indexadas del Banco Interamericano de Desarrollo. Identifica
dos mecanismos, áreas o temas de financiamiento y desarrollo realmente
presentes en las páginas recuperadas. Incluye título y URL para cada uno.
Formula dos preguntas generales de diligencia para una empresa ficticia
que evalúa financiación. No supongas que TLN es beneficiaria o cliente
del BID. No inventes programas, elegibilidad ni montos.
Si el origen no devuelve información verificable, indícalo.
```

## Pregunta para Investopedia — si quedó indexada

```text
Usa exclusivamente la conexión empresarial FinanzasWebCurso con páginas
indexadas de Investopedia. Explica qué es un bono corporativo, qué
representa un cupón y qué significa riesgo crediticio, solo si esos
conceptos se encuentran en las páginas recuperadas. Cita al menos una
página por cada concepto disponible. Luego describe qué preguntas
pedirías verificar en el caso ficticio TLN, sin presentar el contenido
externo como evidencia de que su emisión está aprobada.
Si faltan páginas, decláralo y no inventes fuentes.
```

## Comprobación útil para el instructor

- **Origen:** el agente muestra `FinanzasWebCurso` o el nombre real de la conexión **dentro de Conocimiento**; no basta que aparezca en Microsoft 365 Admin.
- **Citas:** al abrir una URL citada se encuentra el dato o el concepto usado; la respuesta no puede atribuir contenido inexistente al sitio.
- **Separación de fuentes:** los indicadores 2025 de TLN solo provienen de F1–F3; las páginas públicas aportan contexto, no validan cifras de TLN.
- **Limitación:** el conector indexa contenido mediante rastreo, **no consulta información en vivo** y no ejecuta acciones de escritura.
- **Estado:** una conexión sin páginas indexadas, no seleccionable en Agent Builder o sin citas verificables **no se considera funcional**.

Documentación oficial: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/enterprise-web-connector
