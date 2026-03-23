# Matriz de Casos de Prueba: TASK-2026-01771
## Proyecto: Monitoreo y Generación de Rutas - Datos Conductor

| Categoría | ID | Escenario de Prueba | Precondición | Pasos | Resultado Esperado | Prioridad | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **POSITIVO** | CP-POS-001 | Visibilidad de Iconos en Rutas | Ruta con conductor asignado. | Ingresar 'Buscar' en Rutas. | Iconos Foto/Teléfono son visibles. | Alta | ✅ APROBADO |
| **POSITIVO** | CP-POS-002 | Visualización de Foto del Conductor | Registro con icono de foto activo. | Click icono foto -> Comparar con Foto en [Employee HR-EMP-09364](https://erp-git-prod.shalom.com.pe/app/employee/HR-EMP-09364). | La foto coincida con la del maestro de empleados. | Media | ✅ APROBADO (MATCH) |
| **POSITIVO** | CP-POS-003 | Visualización de Teléfonos (Ambos) | Conductor con nro personal y corporativo. | Click icono tel -> Comparar 'Personal' con Celular en Employee y 'Corporativo' con [Líneas Móviles 2](https://erp-git-prod.shalom.com.pe/app/lineas-moviles-2) (filtros por Responsable). | Los números coincidan con el maestro de empleados y líneas móviles corporativas. | Alta | ✅ APROBADO (MATCH) |
| **POSITIVO** | CP-POS-004 | Acceso a "Conductores" en Monitoreo | Estar en el módulo de Monitoreo. | Buscar la opción/link "Conductores". | La opción es visible y funcional dentro del módulo. | Alta | ⏳ Pendiente |
| **NEGATIVO** | CP-NEG-001 | Ocultamiento de Iconos sin Conductor | Ruta SIN conductor asignado. | Ingresar a 'Generar Rutas' y ubicar un registro vacío de conductor. | Los iconos de Foto y Teléfono NO deben mostrarse. | Alta | ⏳ Pendiente |
| **BORDE** | CP-BOR-001 | Conductor sin foto registrada | Conductor asignado pero sin archivo de imagen. | Hacer clic en el icono de la foto. | El modal se abre pero se muestra vacío o con placeholder, sin romper la UI. | Baja | ⏳ Pendiente |
| **BORDE** | CP-BOR-002 | Conductor sin teléfonos registrados | Conductor asignado sin números en BD. | Hacer clic en el icono de teléfono. | El modal muestra: "Personal: -" y "Corporativo: -". | Media | ⏳ Pendiente |
| **BORDE** | CP-BOR-003 | Conductor con un solo teléfono | Solo tiene nro personal o solo corporativo. | Hacer clic en el icono de teléfono. | Muestra el número existente y "-" para el faltante. | Media | ⏳ Pendiente |
| **UI/UX** | CP-UI-001 | Interactividad de Modales | Modal abierto. | Hacer clic fuera del modal o en el botón cerrar. | El modal se cierra correctamente y permite seguir navegando. | Media | ⏳ Pendiente |

---
*Matriz generada según estándares ISTQB para el requerimiento de Datos del Conductor.*
