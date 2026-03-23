# Matriz de Pruebas: TASK-2026-01660 (Casilla Legal)
## Reorganizada con resultados al 100% de ejecución.

| Categoría | ID | Escenario | Pre condición | Resultado esperado | Tipo | Prioridad | Estado Ejecución |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **CASOS POSITIVOS** | CP-POS-001 | Visualizar botón "No Derivar" | Registro en estado inicial o pendiente. | Se muestra "No Derivar" en lugar de "Cancelar". | Funcional | Alta | ✅ APROBADO |
| **CASOS POSITIVOS** | CP-POS-002 | Abrir modal de "No Derivar" | Hacer clic en el botón "No Derivar". | Se abre un modal conteniendo el select obligatorio del requerimiento. | Funcional | Alta | ✅ APROBADO |
| **CASOS POSITIVOS** | CP-POS-003 | Seleccionar motivo y guardar | Modal abierto indicando Cancelado / Duplicado etc. | El registro cambia a estado "No Derivado". | Funcional | Crítica | ✅ APROBADO |
| **CASOS POSITIVOS** | CP-POS-004 | Validar ubicación campo motivo | Registro en estado "No Derivado". | El motivo se muestra debajo de "Usuario de registro". | Funcional | Media | ✅ APROBADO |
| **CASOS POSITIVOS** | CP-POS-005 | Ocultar botón en estado Derivado | Solicitud en estado "Derivado". | El botón "No Derivar" no se muestra. | Funcional | Alta | ✅ APROBADO |
| **CASOS POSITIVOS** | CP-POS-006 | Ocultar botón estado No Derivado | Solicitud en estado "No Derivado". | El botón "No Derivar" desaparece y no es interactuable. | Funcional | Alta | ✅ APROBADO |
| **CASOS POSITIVOS** | CP-POS-007 | Visualizar nuevos filtros | Lista Casilla Legal. | Estado "No Derivado" y select "Motivo" están en barra de filtros. | Funcional | Media | ✅ APROBADO |
| **CASOS POSITIVOS** | CP-POS-008 | Validar nueva columna en lista | Lista Casilla Legal. | Columna "Motivo" es visible junto a Estado. | Funcional | Media | ✅ APROBADO |
| **CASOS NEGATIVOS** | CP-NEG-001 | Guardar modal con Motivo vacío | Dejar opción vacía en modal e intentar guardar. | Sistema exige requerimiento y bloquea el guardado. | Funcional | Alta | ✅ APROBADO |
| **CASOS NEGATIVOS** | CP-NEG-002 | Forzar acción de cancelar / API | Bypassear el UI forzando Request al backend. | Backend debería bloquearlo. (Validable vía Red). | Seguridad | Media | Bloqueado QA/Postman |
| **INTEGRACIÓN** | CP-INT-001 | Regularizar registros pasados | Script / Migración ejecutada en Pre-Prod. | Registros pasados "Cancelados" mudan a "No Derivados". | Integración | Crítica | ✅ APROBADO |
| **SEGURIDAD** | CP-SEG-002 | SQL Injection y XSS | Inyectar url (`' OR 1=1 --` / `<script>`) en query. | Filtro limpia o escapa input SQL/XSS sin ejecutarlo. | Seguridad | Media | ✅ APROBADO |
| **REGRESIÓN** | CP-REG-001 | Flujo "Derivar" tradicional | Tomar solicitud y hacer flujo primigenio "Derivar". | Deriva intactamente el doctype secundario de legal. | Regresión | Crítica | ✅ APROBADO |
