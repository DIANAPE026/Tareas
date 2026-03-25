# Matriz de Casos de Prueba: TASK-2026-01801
## Proyecto: SHALOM PRO - AGREGAR VALIDACION DE RUC EN LAS AUTOGESTIONES
### Estándar: ISTQB Certified Tester

| ID | Escenario de Prueba | Categoría | Precondición | Datos de Prueba | Pasos | Resultado Esperado | Prioridad | Severidad | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **CP-POS-001** | Autogestión exitosa (Devolución) usando perfil Empresa (RUC) | POSITIVO | Usuario logueado con perfil Empresa en pro.shalom.pe. La guía pertenece a dicho RUC como remitente. | Guía: 73893181 (o una válida para el RUC) | 1. Ingresar a la opción "Devolución de Mercadería".<br>2. Ingresar el número de guía.<br>3. Ejecutar la validación. | El sistema reconoce el RUC como remitente legítimo y permite continuar la gestión sin alertas de error. | Alta | Crítica | ⏳ PENDIENTE |
| **CP-POS-002** | Validación de cuenta Persona Natural con Empresa vinculada | POSITIVO | Usuario (PN) tiene una empresa vinculada. El RUC de la empresa es el remitente de la guía a gestionar. | Guía a nombre del RUC de la empresa vinculada | 1. Ingresar con cuenta de Persona Natural.<br>2. Intentar gestionar guía del RUC asociado.<br>3. Ejecutar validación. | El sistema asimila el vínculo y aprueba la autogestión de manera transparente sin bloqueos. | Alta | Alta | ⏳ PENDIENTE |
| **CP-POS-003** | Retrocompatibilidad: Autogestión con DNI/CE | POSITIVO | Usuario Persona Natural y guía emitida a su DNI/CE. | Guía clásica con DNI | 1. Ingresar módulo de Autogestión (ej. Reparto a domicilio).<br>2. Validar guía. | La validación clásica por DNI o CE sigue funcionando correctamente sin verse afectada por la inclusión del RUC. | Alta | Crítica | ⏳ PENDIENTE |
| **CP-NEG-001** | Rechazo por RUC que NO es el remitente titular | NEGATIVO | Usuario Empresa logueado.| Guía cuyo remitente es OTRO RUC u OTRO DNI. | 1. Intentar hacer un "Cambio de Destino".<br>2. Validar identidad para esa guía. | El sistema muestra la alerta "SOLO EL REMITENTE PUEDE GESTIONAR" o deniega el paso, protegiendo la carga. | Alta | Alta | ⏳ PENDIENTE |
| **CP-NEG-002** | Manejo de caracteres en RUC (Ej. 10 y 20 combinados) | NEGATIVO | Usuario en formulario de datos. | RUC con formato alterado | 1. Ingresar un formato irregular si el campo lo permite. | El sistema detecta el error de validación de documento y notifica formato inválido en lugar de explotar. | Media | Baja | ⏳ PENDIENTE |
| **CP-REG-001** | Verificación cruzada en todos los módulos de autogestión | REGRESIÓN | Usuario con perfil Empresa válido. | RUC remitente en guías distintas | 1. Realizar flujo hasta validación en: Agregar Contacto, Actualización Clave, Retención de Entrega. | En todos los 6 módulos afectados, la barrera validatoria dual acepta el RUC satisfactoriamente. | Alta | Alta | ⏳ PENDIENTE |

---
*Matriz diseñada bajo lineamientos de ISTQB (International Software Testing Qualifications Board).*
