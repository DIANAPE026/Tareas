# Matriz de Casos de Prueba: TASK-2026-01742
## Proyecto: REPORTE AEREO - DESCARGA DE REPORTE USUARIOS HABILITADOS
### Estándar: ISTQB Certified Tester

| ID | Escenario de Prueba | Categoría | Precondición | Datos de Prueba | Pasos | Resultado Esperado | Prioridad | Severidad | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **CP-POS-001** | Visibilidad de "Cierre Aéreo" | POSITIVO | Usuario en "lista de privilegios embarque aéreo" y terminal con soporte aéreo. | Credenciales de usuario aéreo, ID de Terminal Aérea. | 1. Ingresar al ERP.<br>2. Navegar a /reportes. | La opción "Cierre Aéreo" es visible y seleccionada por defecto. | Alta | Media | ⏳ PENDIENTE |
| **CP-POS-002** | Descarga de Reporte de Cierre | POSITIVO | Usuario habilitado en sección de reportes. | Rango de fechas (hoy), filtros de operación. | 1. Seleccionar filtros.<br>2. Click en "Descargar Reporte". | El archivo se descarga en formato .xlsx / .pdf sin errores. | Alta | Alta | ⏳ PENDIENTE |
| **CP-POS-003** | Integridad de Datos en Reporte | POSITIVO | Registro de operaciones aéreas previas en BD. | Manifiestos aéreos del día. | 1. Descargar reporte.<br>2. Comparar totales con la vista de 'aereo'. | Los totales y detalles en el reporte coinciden con los del sistema. | Media | Media | ⏳ PENDIENTE |
| **CP-NEG-001** | Restricción para Usuario No Autorizado | NEGATIVO | Usuario NO está en "lista de privilegios embarque aéreo". | Credenciales de usuario administrativo estándar. | 1. Ingresar a /reportes. | La opción "Cierre Aéreo" NO debe ser visible en el menú. | Alta | Alta | ⏳ PENDIENTE |
| **CP-NEG-002** | Restricción por Terminal No Aérea | NEGATIVO | Usuario habilitado pero asignado a terminal SIN soporte aéreo. | ID de Terminal Terrestre. | 1. Cambiar de terminal.<br>2. Ingresar a /reportes. | La opción "Cierre Aéreo" se oculta o se deshabilita. | Alta | Media | ⏳ PENDIENTE |
| **CP-BOR-001** | Usuario con Múltiples Privilegios | BORDE | Usuario con acceso a reportes terrestres y aéreos. | Roles combinados. | 1. Ingresar a /reportes. | "Cierre Aéreo" se mantiene como la opción prioritaria por defecto según lógica de negocio. | Media | Baja | ⏳ PENDIENTE |
| **CP-BOR-002** | Cambio de Terminal en Sesión Activa | BORDE | Sesión iniciada en terminal aérea. | Cambio dinámico de sucursal. | 1. Cambiar terminal.<br>2. Verificar menú de reportes sin recargar página completa. | El sistema actualiza los permisos de reporte dinámicamente. | Media | Baja | ⏳ PENDIENTE |
| **CP-UI-001** | Consistencia de Inter

