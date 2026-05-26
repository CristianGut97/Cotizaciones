# SOFTWARE REQUIREMENTS SPECIFICATION (SRS)
## Sistema de Gestión de Cotizaciones

### 1. Descripción General
El Sistema de Gestión de Cotizaciones es una aplicación backend diseñada para permitir la creación, gestión, seguimiento y conversión de cotizaciones en órdenes o proyectos.

### 2. Objetivos del Proyecto
**Objetivo General:** Desarrollar un sistema backend robusto, escalable y bien estructurado que permita gestionar cotizaciones empresariales de manera profesional.
**Objetivos Específicos:**
- Implementar Clean Architecture.
- Aplicar principios SOLID.
- Autenticación y autorización basada en roles.
- Documentación automática (OpenAPI).
- Pruebas unitarias e integración.

### 3. Alcance del Proyecto
**Incluye:**
- Gestión de usuarios, clientes y productos.
- Creación y seguimiento de cotizaciones.
- Cálculo automático de impuestos y descuentos.
- Exportación a PDF.
**No Incluye (Fase 1):**
- Pasarela de pagos.
- Facturación electrónica.

### 4. Modelo de Datos
- **Usuario:** id, nombre, email, password_hash, rol, activo.
- **Cliente:** id, nombre_empresa, nit, telefono, email, direccion.
- **Producto:** id, nombre, descripcion, precio_unitario, tipo, activo.
- **Cotización:** id, numero, cliente_id, usuario_id, subtotal, impuestos, descuento, total, estado, fechas.
- **DetalleCotización:** id, cotizacion_id, producto_id, cantidad, precio_unitario, subtotal.

### 5. Reglas de Negocio
- Número de cotización único.
- Total = Subtotal + Impuestos - Descuento.
- Requiere al menos un producto para aprobación.
- No modificable una vez aprobada.
- Descuento < Subtotal.
