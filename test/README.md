1. Descripción General

El Sistema de Gestión de Cotizaciones es una aplicación backend diseñada para permitir la creación, gestión, seguimiento y conversión de cotizaciones en órdenes o proyectos.

El sistema estará orientado a empresas que requieran:

Generar cotizaciones formales para clientes

Calcular automáticamente costos, impuestos y descuentos

Gestionar estados de aprobación

Mantener historial y trazabilidad

Exportar cotizaciones en formato PDF

Administrar clientes, productos y usuarios

2. Objetivos del Proyecto
Objetivo General

Desarrollar un sistema backend robusto, escalable y bien estructurado que permita gestionar cotizaciones empresariales de manera profesional.

Objetivos Específicos

Implementar arquitectura limpia (Clean Architecture)

Aplicar principios SOLID

Implementar autenticación y autorización basada en roles

Implementar documentación automática (OpenAPI)

Manejar persistencia con base de datos relacional

Implementar pruebas unitarias y de integración

Preparar el sistema para despliegue en la nube

3. Alcance del Proyecto
Incluye

Gestión de usuarios

Gestión de clientes

Gestión de productos o servicios

Creación de cotizaciones

Cálculo automático de impuestos

Manejo de descuentos

Estados de cotización

Conversión de cotización a orden

Exportación a PDF

API REST documentada

No Incluye (Fase 1)

Pasarela de pagos

Facturación electrónica

Integración con ERP externo

Frontend complejo (solo documentación y pruebas con Swagger)

4. Arquitectura del Sistema

Se implementará bajo un enfoque de arquitectura por capas:

Presentation Layer (API REST)

Application Layer (Casos de uso)

Domain Layer (Entidades y reglas de negocio)

Infrastructure Layer (Base de datos, servicios externos)

Patrón sugerido:

Repository Pattern

Dependency Injection

DTOs para transferencia de datos

Validación con Pydantic

5. Tecnologías a Utilizar

Python

Framework web moderno para APIs

ORM para base de datos relacional

Base de datos SQLite (fase inicial) → PostgreSQL (producción)

Generación de PDF

Docker (opcional)

Testing framework

6. Modelo de Datos Inicial
Usuario

id

nombre

email

password_hash

rol (admin, vendedor, supervisor)

fecha_creacion

activo

Cliente

id

nombre_empresa

nit

telefono

email

direccion

fecha_creacion

Producto / Servicio

id

nombre

descripcion

precio_unitario

tipo (producto/servicio)

activo

Cotización

id

numero_cotizacion

cliente_id

usuario_id

subtotal

impuestos

descuento

total

estado (borrador, enviada, aprobada, rechazada, vencida)

fecha_creacion

fecha_vencimiento

DetalleCotizacion

id

cotizacion_id

producto_id

cantidad

precio_unitario

subtotal

7. Reglas de Negocio

El número de cotización debe ser único.

El total se calcula automáticamente:
total = subtotal + impuestos - descuento

No se puede aprobar una cotización sin al menos un producto.

No se puede modificar una cotización en estado "aprobada".

Las cotizaciones vencidas cambian automáticamente de estado.

Solo usuarios con rol "admin" pueden eliminar registros.

Los descuentos no pueden superar el subtotal.

8. Endpoints Principales (API REST)
Autenticación

POST /login

POST /register

Clientes

POST /clientes

GET /clientes

GET /clientes/{id}

PUT /clientes/{id}

DELETE /clientes/{id}

Productos

POST /productos

GET /productos

PUT /productos/{id}

DELETE /productos/{id}

Cotizaciones

POST /cotizaciones

GET /cotizaciones

GET /cotizaciones/{id}

PUT /cotizaciones/{id}

POST /cotizaciones/{id}/aprobar

POST /cotizaciones/{id}/rechazar

GET /cotizaciones/{id}/pdf

9. Seguridad

Autenticación basada en JWT

Hash seguro de contraseñas

Protección contra inyección SQL (ORM)

Validación de entrada estricta

Manejo adecuado de errores

10. Manejo de Errores

El sistema debe:

Retornar códigos HTTP correctos

Retornar mensajes estructurados

Registrar errores críticos

Manejar excepciones globales

Formato estándar de error:

{
  "error": "Descripción del error",
  "status_code": 400,
  "timestamp": "ISO8601"
}

11. Pruebas

Se deben incluir:

Pruebas unitarias de reglas de negocio

Pruebas de endpoints

Pruebas de autenticación

Cobertura mínima esperada: 70%

12. Documentación

Documentación automática de la API

README profesional

Diagrama de arquitectura

Diagrama entidad-relación

Ejemplos de uso con curl

13. Escalabilidad Futura

Multiempresa (multi-tenant)

Integración con facturación electrónica

Integración con pagos

Dashboard estadístico

Control de inventario

Firma digital
