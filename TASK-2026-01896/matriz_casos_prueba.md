# Matriz de Casos de Prueba: TASK-2026-01896
## Proyecto: CASILLA LEGAL - QUITAR LA REDIRECCION A SOLICITUD CN
### Estándar: ISTQB Certified Tester

| ID | Escenario de Prueba | Categoría | Precondición | Datos de Prueba | Pasos | Resultado Esperado | Prioridad | Severidad | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **CP-POS-001** | Redirección directa sin modal para "Cartas Notariales" | POSITIVO | Usuario logueado con permisos a Casilla Legal.<br>Registro en derivación (CARTAS NOTARIALES). | Entidad "CARTAS NOTARIALES" | 1. Ingresar a Casilla Legal.<br>2. Ubicar el registro.<br>3. Hacer clic en "Derivar". | El sistema no muestra el modal de destino y redirige automáticamente a Descargos Cartas Notariales. | Alta | Alta | ✅ ÉXITO |
| **CP-POS-002** | Validación de "ID Documento" autocompletado | POSITIVO | Haber ejecutado CP-POS-001.<br>Conocer el ID original. | ID de Casilla Legal origen | 1. Revisar el formulario destino generado en Descargos. | El campo "ID Documento" se autocompleta con el ID originado desde Casilla Legal. | Media | Media | ✅ ÉXITO |
| **CP-NEG-001** | Intento de derivar sin estado válido | NEGATIVO | Registro "CARTAS NOTARIALES" inactivo o ya derivado. | Estado inactivo/completado | 1. Ingresar a Casilla Legal.<br>2. Forzar clic en "Derivar". | El sistema rechaza la redirección ("Estado inválido") o el botón está inactivo. | Media | Alta | ✅ ÉXITO |
| **CP-NEG-002** | Derivación con otra entidad presenta el modal clásico | NEGATIVO | Registro con entidad distinta a "CARTAS NOTARIALES". | Entidad "Denuncias" o afín | 1. Ingresar a Casilla Legal.<br>2. Hacer clic en "Derivar". | El sistema no emite redirección automática, sino que abre el modal clásico. | Alta | Alta | ✅ ÉXITO |
| **CP-BOR-001** | Redirección durante expiración de sesiones | BORDE | Sesión próxima a expirar y registro listo. | Timeout de sesión | 1. Esperar al timeout de UI.<br>2. Hacer clic en "Derivar". | El sistema intercepta y redirige al Login protegiendo los estados. | Baja | Media | ⏳ PENDIENTE |
| **CP-BOR-002** | Redirección múltiple concurrente | BORDE | Registro abierto en 2 pestañas distintas. | N/A | 1. Clic en "Derivar" al unísono. | Una transacción avanza y la otra redirige bloqueando doble ejecución no deseada en BD. | Baja | Baja | ⏳ PENDIENTE |
| **CP-INT-001** | Sincronización transparente de parámetros a Descargos | INTEGRACIÓN | Traza de red abierta en CP-POS-001. | Parámetros de GET/POST | 1. Confirmar redirección.<br>2. Revisar payload transferido. | Los parámetros (ej. `id_origen`) viajan y son capturados exitosamente por Descargos. | Alta | Crítica | ⏳ PENDIENTE |
| **CP-INT-002** | Creación completa del registro de Descargo post-derivación | INTEGRACIÓN | Superar la redirección (CP-POS-001). | Formulario de Descargos completo | 1. Llenar los campos restantes en la UI.<br>2. Guardar. | Front y Backend guardan el registro final atado a Casilla Legal sin problemas de llaves foráneas. | Alta | Crítica | ✅ ÉXITO |
| **CP-SEG-001** | Prevención de Forced Browsing en API | SEGURIDAD | Usuario conectado con Postman/CURL asimilado al portal. | Payload modificado forzando entidad falsa | 1. Interceptar un requets antiguo y forzarlo como "CARTAS NOTARIALES" sin payload clásico. | Backend rechaza request con error técnico defendiendo el bypass manual de la validación. | Media | Alta | ⏳ PENDIENTE |
| **CP-SEG-002** | Validación estricta de Roles UI (Access Control) | SEGURIDAD | Cuenta SOLO con acceso a Casilla Legal (SIN Descargos). | Credenciales restrictivas | 1. Intentar clic en "Derivar" a "CARTAS NOTARIALES". | El enrutador bloquea el acceso informando 403 (Forbidden / Permisos). | Media | Media | ⏳ PENDIENTE |
| **CP-REG-001** | Eliminación de "Casilla Legal" en Solicitudes (CRUD Completo) | REGRESIÓN | Usuario con rol de Solicitud de Cartas Notariales. | N/A | 1. Validar vista de Creación.<br>2. Validar Edición. | Campo "Casilla Legal" no renderiza y no bloquea guardados en BD a falta del valor. | Media | Baja | ✅ ÉXITO |
| **CP-REG-002** | Componente Modal de derivación invicto (sin fricción externa) | REGRESIÓN | Usar registros ordinarios (ej. Reclamos). | N/A | 1. Navegar por modal.<br>2. Completar de manera clásica. | Flujo ordinario de las demás dependencias funciona tal cual sin efectos colaterales. | Alta | Crítica | ✅ ÉXITO |
| **CP-E2E-001** | Ciclo de vida completo "Cartas Notariales" | END TO END | Creación en Base de Casilla Legal para mock. | N/A | 1. Ingresar.<br>2. Derivar.<br>3. Redirigir.<br>4. Llenar Descargo.<br>5. Guardar éxito total. | El flujo cruza todos los estadíos sin caídas de UI, cierres de sesión ni excepciones de Backend. | Crítica | Crítica | ✅ ÉXITO |
| **CP-PER-001** | Tiempo de redirección UI menor (Salto veloz) | PERFORMANCE | Consola de DevTools en Throttling regular. | N/A | 1. Click y medir en Profile | El salto SPA (Single Page Apps) transcurre en `< 2` segundos. | Baja | Menor | ⏳ PENDIENTE |
| **CP-PER-002** | Carga del formulario Solicitud de Cartas Notariales optimizado | PERFORMANCE | Lighthouse audit para Solicitud. | N/A | 1. Ingresar a la ruta del formulario de Solicitudes limpiado. | El tiempo del componente reduce al restarse un elemento reactivo ligado a bindings JS. | Baja | Menor | ⏳ PENDIENTE |

---
*Matriz diseñada bajo lineamientos de ISTQB (International Software Testing Qualifications Board).*

## Evidencias
- [CP-POS-001 y CP-POS-002](EVIDENCIAS/CP-POS-001_CP-POS-002_Derivacion_Automatica.webp)
- [CP-E2E-001 y CP-REG-001](EVIDENCIAS/CP-E2E-001_CP-REG-001_Pruebas_Flujo_Completo.webp)
- [CP-NEG-002 y CP-REG-002](EVIDENCIAS/CP-NEG-002_CP-REG-002_Modal_Clasico_Con_Roles.webp)
