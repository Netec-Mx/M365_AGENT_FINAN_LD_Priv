# Control técnico del instructor — Enterprise Websites

Este recurso es una **lista previa de comprobaciones**, no una actividad adicional para participantes. Ejecutar todas las verificaciones **antes** de los cinco minutos destinados a la práctica 4.

## Preparación de una sola conexión

1. Entrar en https://admin.microsoft.com/ con permisos de **AI Administrator** y abrir **Copilot > Connectors > Gallery > Enterprise Websites**.
2. Proponer el nombre de conexión `FinanzasWebCurso` y elegir **una URL raíz pública** de la ficha [05_Fuentes_web_financieras.md](05_Fuentes_web_financieras.md). La conexión puede tener otro nombre; si cambia, actualizar los prompts de la práctica.
3. Seleccionar autenticación **None** para un sitio público que no exija inicio de sesión; no introducir credenciales del sitio si no son necesarias.
4. Verificar el efecto de las redirecciones: el conector solo sigue redirecciones **dentro del mismo hostname**. Una página de desafío de seguridad en otro dominio no es un origen indexable útil.
5. Elegir rastreo con sitemap **solo si el sitemap está disponible y contiene las páginas que se quieren consultar**; de otro modo, comprobar el resultado del rastreo profundo del sitio.
6. Confirmar que la conexión publicada ha indexado páginas con **contenido legible** y sin errores de rastreo relevantes. Una conexión creada pero vacía **no está lista**.
7. Comprobar que el índice es **visible para todos los usuarios de la organización**, que es el permiso documentado para este conector; utilizar únicamente páginas públicas.
8. Abrir el agente `Asistente de Emision TLN` en **Agent Builder** con la identidad del instructor: ir a **Conocimiento > Elegir otros orígenes de datos**, localizar el conector y seleccionar la conexión preparada.
9. Ejecutar el prompt del sitio seleccionado; comprobar al menos **una cita abierta** que demuestre el contenido recuperado. Distinguir el origen empresarial de la búsqueda web general.
10. Dejar el agente listo para mostrar el recorrido o, si el ejercicio exige que el instructor lo agregue en vivo, confirmar que podrá repetirlo en menos de dos minutos.

## Criterios de bloqueo

- **Error de rastreo** por `robots.txt`, páginas dinámicas no compatibles, desafío anti-bot o redirección a otro hostname: **no indexar** ese sitio; validar otro antes del curso.
- **Conexión sin contenido indexado:** no pasar a la demostración.
- **Conexión en Microsoft 365 Admin, pero ausente de Agent Builder:** no declarar que el agente ya usa el conector.
- **Respuesta sin referencias a páginas del conector:** no presentarla como evidencia de integración, incluso si el texto parece correcto.
- **Fallo en los tres candidatos:** informar que la práctica 4 está técnicamente bloqueada y mantener el tiempo de demostración para explicar la restricción, sin simular un éxito.

**Fuentes oficiales:**

- https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/enterprise-web-connector
- https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge
- https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/manage-connector
