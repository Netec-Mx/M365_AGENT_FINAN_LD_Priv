# Práctica 2. Conciliación de datos simulados con Finance Agent

## Objetivo de la práctica:

Al finalizar la práctica, serás capaz de:

- Ejecutar una conciliación asistida con **Finance Agent** entre dos tablas financieras de Excel.
- Identificar coincidencias exactas y diferencias demostrables sin asumir sus causas contables.
- Completar un modelo sencillo de caja en Excel y analizar el efecto de las partidas por revisar.

## Duración aproximada:

- **36 minutos.**

## Tabla de ayuda:

| Parámetro | Valor | Uso |
|---|---|---|
| Libro de datos | [Conciliacion_TLN.xlsx](recursos/Conciliacion_TLN.xlsx) | Archivo de entrada de Finance Agent. |
| Tabla del libro mayor | `TablaMayor` — hoja `Mayor` | Movimientos contables simulados de octubre de 2026. |
| Tabla del extracto | `TablaBanco` — hoja `Banco` | Movimientos bancarios simulados del mismo mes. |
| Hoja del modelo | `Modelo` | Escenarios de caja con celdas a completar. |
| Campo de correspondencia | `Referencia` en ambas tablas | Clave de mapeo en Finance Agent. |
| Campo monetario | `Importe_USD` en ambas tablas | Clave monetaria con signos iguales. |
| Saldo inicial simulado | **2 000 000 USD** | Supuesto para el modelo. |

> **Requisito operativo:** Esta práctica exige el complemento oficial **Finance Agent** con **Financial Reconciliation** visible. No es equivalente a «Copilot en Excel» ni a una comparación manual. Comprobar primero [SETUP_GUIDE.md](../SETUP_GUIDE.md). Microsoft documenta limitaciones de disponibilidad y región para esta función.

## Instrucciones

### Tarea 1. Abrir el libro y verificar la estructura de los datos (5 minutos)

**Paso 1.** Descargar [Conciliacion_TLN.xlsx](recursos/Conciliacion_TLN.xlsx), abrirlo en **Excel para Microsoft 365** con el complemento de Finance Agent disponible y guardar una **copia de trabajo** en OneDrive o en la ubicación institucional permitida.

**Paso 2.** Seleccionar las hojas **Mayor** y **Banco**. Comprobar que las tablas tienen los encabezados `Referencia`, `Fecha`, `Concepto`, `Importe_USD` y que contienen **8 movimientos** y **9 movimientos**, respectivamente.

**Paso 3.** Confirmar que `Importe_USD` contiene números, no importes almacenados como texto. Los cobros son positivos y los pagos y cargos son negativos. No cambiar signos ni códigos de referencia.

**Paso 4.** Abrir la hoja **Modelo** y localizar las celdas de cálculo resaltadas en amarillo. Conservarla sin fórmulas hasta finalizar la conciliación.

### Tarea 2. Ejecutar Financial Reconciliation en Finance Agent (12 minutos)

**Paso 1.** Seleccionar **Inicio > Finance Agent** en la cinta de Excel para abrir el panel lateral. Elegir **Financial Reconciliation**.

**Paso 2.** Revisar en la tarjeta **Tables** que aparecen `TablaMayor` y `TablaBanco` (una por cada hoja). Si el agente eligió otra tabla u hoja, retirarla con **X** y utilizar **Add** para agregar las dos tablas correctas.

**Paso 3.** Abrir la tarjeta **Keys**. Inspeccionar las sugerencias de Finance Agent y establecer explícitamente los siguientes vectores; mantener o editar la recomendación si es necesario:

| Vector de conciliación | TablaMayor | TablaBanco |
|---|---|---|
| Mapping key / Clave de correspondencia | `Referencia` | `Referencia` |
| Monetary key / Clave monetaria | `Importe_USD` | `Importe_USD` |

**Paso 4.** Eliminar reglas adicionales que puedan transformar la comparación (tolerancia monetaria, coincidencia parcial o fecha) si fueron sugeridas y no corresponden a este ejercicio. El objetivo es distinguir la discrepancia real de **200 USD** en `OP-1005`; una tolerancia podría ocultarla.

**Paso 5.** Incluir `Fecha` y `Concepto` como columnas de referencia opcionales cuando la interfaz lo permita. Utilizarlas solo como **contexto**, no como claves de emparejamiento. Conservar la vista resumida del reporte para el primer análisis.

**Paso 6.** Seleccionar **Reconcile data / Conciliar datos** y abrir el reporte de conciliación generado en el libro de Excel. Verificar que Finance Agent produjo un reporte y, cuando corresponda, copias de las hojas de origen con sufijo `_reconciled`.

> **Nota:** El propio Finance Agent puede variar la clasificación según los vectores elegidos. La referencia del caso es la **comparación exacta por `Referencia` e `Importe_USD`**; no interpretar cualquier etiqueta generada como prueba de causa contable.

### Tarea 3. Auditar el resultado con las tablas originales (11 minutos)

**Paso 1.** Inspeccionar las secciones **Matched / Coincidencias**, **Unmatched / No coincidentes** y, si aparece, **Potentially matched** del reporte. Identificar las transacciones por `Referencia`.

**Paso 2.** Contrastar con ambas hojas originales los siguientes resultados verificables:

| Referencia | Dato del mayor | Dato del banco | Conclusión por comparación directa |
|---|---:|---:|---|
| `OP-1001`, `OP-1002`, `OP-1003`, `OP-1004`, `OP-1006`, `OP-1007` | Coincide | Coincide | **6 pares** con referencia e importe idénticos. |
| `OP-1005` | -12 200 USD | -12 000 USD | La misma referencia tiene **200 USD de diferencia**. |
| `OP-1008` | -15 000 USD | Sin registro | Partida presente **solo en el mayor**. |
| `BNK-5001` | Sin registro | -350 USD | Comisión presente **solo en el banco**. |
| `OP-1009` | Sin registro | +5 000 USD | Abono presente **solo en el banco**. |

**Paso 3.** Seleccionar `OP-1005` en el informe y, si está disponible, usar **Insights > Troubleshoot transactions** para revisar la explicación sugerida. Identificar la diferencia monetaria como comprobada, pero no afirmar si se debe a un error de digitación, descuento o cargo hasta consultar justificantes.

**Paso 4.** Revisar `OP-1008`, `BNK-5001` y `OP-1009` por separado. Distinguir **movimiento ausente** de **ajuste autorizado**: la conciliación por sí sola no permite reconocer ingresos, gastos ni asientos.

**Paso 5.** Consultar la síntesis generada por Finance Agent. Si presenta como hechos las causas posibles o afirma conciliación total, corregir la interpretación en el propio documento de trabajo con las cuatro partidas anteriores.

### Tarea 4. Completar y analizar el modelo de caja (8 minutos)

**Paso 1.** Regresar a la hoja `Modelo` del libro **de trabajo**. Confirmar el saldo inicial didáctico de **2 000 000 USD** en `B5` y el cargo observado de **-350 USD** en `B6`. El segundo es un dato bancario pendiente de validación, no un asiento aprobado.

**Paso 2.** Completar las celdas indicadas de la hoja `Modelo` con las siguientes fórmulas. Usar `SUMA` si Excel está configurado en español o `SUM` si acepta los nombres de funciones en inglés.

| Celda | Fórmula o cálculo | Significado |
|---|---|---|
| `B8` | `=SUMA(Mayor!D6:D13)` | Flujo neto del mayor. |
| `B9` | `=SUMA(Banco!D6:D14)` | Flujo neto del banco. |
| `B10` | `=B9-B8` | Diferencia de flujos. |
| `B12` | `=B5+B8` | Caja según mayor. |
| `B13` | `=B5+B9` | Caja según banco. |
| `B14` | `=B12+B6` | Escenario ilustrativo si se reconoce la comisión. |
| `B15` | `=B13-B14` | Diferencia remanente por explicar. |

**Paso 3.** Verificar estos resultados por cálculo aritmético y con los movimientos originales:

| Resultado | Valor esperado |
|---|---:|
| Flujo neto de mayor (`B8`) | **126 500 USD** |
| Flujo neto de banco (`B9`) | **146 350 USD** |
| Diferencia banco - mayor (`B10`) | **19 850 USD** |
| Saldo según mayor (`B12`) | **2 126 500 USD** |
| Saldo según banco (`B13`) | **2 146 350 USD** |
| Escenario mayor tras comisión (`B14`) | **2 126 150 USD** |
| Diferencia restante (`B15`) | **20 200 USD** |

**Paso 4.** Interpretar la diferencia restante: **15 000 USD** por `OP-1008` no encontrado en el banco, **5 000 USD** de `OP-1009` no encontrado en el mayor y **200 USD** por `OP-1005`. Explicar en una celda de comentario o al final de la hoja `Modelo` que **ninguna de estas partidas debe ajustarse automáticamente** sin soporte documental. Guardar el archivo con sus fórmulas y el informe de Finance Agent.

### Resultado esperado

El libro de trabajo contiene un **reporte de Financial Reconciliation generado desde el complemento Finance Agent** con seis coincidencias exactas y las discrepancias `OP-1005`, `OP-1008`, `BNK-5001` y `OP-1009` identificadas y contrastadas. La hoja `Modelo` muestra una diferencia original de **19 850 USD**, una proyección de caja antes y después de considerar ilustrativamente la comisión y un remanente de **20 200 USD** pendiente de explicación. El participante diferencia hallazgos numéricos de causas y ajustes no acreditados. Si Finance Agent no está habilitado, el análisis del libro puede revisarse, pero no se considera ejecutada la práctica con la herramienta prevista.

Documentación oficial: [Reconcile data with Finance Agent](https://learn.microsoft.com/en-us/copilot/finance/reconcile/reconcile-data) · [Reconciliation in Excel](https://learn.microsoft.com/en-us/copilot/finance/reconcile/reconcile-overview) · [Preguntas frecuentes y límites de Finance Agent](https://learn.microsoft.com/en-us/copilot/finance/responsible-ai/responsible-ai-faq-for-reconciliation).
