# 🚀 Sistema de Gestión de Cotizaciones

¡Bienvenido al **Sistema de Gestión de Cotizaciones**! Una solución robusta y escalable diseñada para transformar la manera en que las empresas gestionan sus procesos comerciales, desde el primer contacto hasta el cierre de la venta.

---

## 🎯 Objetivo del Proyecto

Este sistema backend está construido con un enfoque en **Arquitectura Limpia (Clean Architecture)** y principios **SOLID**, garantizando un código mantenible, testeable y preparado para el crecimiento empresarial.

### ✨ Características Principales
- 👥 **Gestión de Usuarios:** Autenticación y autorización basada en roles (Admin, Vendedor, Supervisor).
- 🏢 **Gestión de Clientes:** Directorio completo de empresas y contactos.
- 📦 **Catálogo de Productos/Servicios:** Control de precios y descripciones.
- 📄 **Cotizaciones Inteligentes:**
  - Cálculo automático de subtotal, impuestos y descuentos.
  - Gestión de estados (Borrador, Enviada, Aprobada, Rechazada, Vencida).
  - Conversión directa a órdenes.
- 📑 **Exportación PDF:** Generación profesional de documentos para clientes.
- 🔐 **Seguridad:** Protección con JWT y hashing de contraseñas.
- 📚 **Documentación:** API documentada automáticamente con Swagger/OpenAPI.

---

## 🏗️ Arquitectura y Tecnologías

El proyecto sigue una estructura de capas para separar las responsabilidades:

- **Presentation:** FastAPI (Endpoints y validación con Pydantic).
- **Application:** Lógica de casos de uso.
- **Domain:** Entidades de negocio y reglas nucleares.
- **Infrastructure:** Persistencia con SQLAlchemy y servicios externos.

### 🛠️ Stack Tecnológico
- **Lenguaje:** Python 3.10+
- **Framework:** [FastAPI](https://fastapi.tiangolo.com/)
- **ORM:** [SQLAlchemy](https://www.sqlalchemy.org/)
- **Base de Datos:** SQLite (Desarrollo) / PostgreSQL (Producción)
- **Seguridad:** OAuth2 + JWT
- **Reportes:** ReportLab / WeasyPrint (PDF)

---

## 🚀 Inicio Rápido

### 1️⃣ Requisitos Previos
- Python 3.10 o superior.
- Git.

### 2️⃣ Instalación
```bash
# Clonar el repositorio
git clone <url-del-repo>
cd Cotizaciones

# Crear y activar entorno virtual
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate

# Instalar dependencias
pip install -r requirements.txt
```

### 3️⃣ Ejecución
```bash
uvicorn app.main:app --reload
```
Visita `http://127.0.0.1:8000/docs` para ver la documentación interactiva.

---

## 📊 Modelo de Datos (Resumen)
- **Usuario:** Identidad y roles.
- **Cliente:** Datos fiscales y contacto.
- **Producto/Servicio:** Precios y disponibilidad.
- **Cotización:** Cabecera con totales y fechas.
- **DetalleCotización:** Líneas de productos y cantidades.

---

## 🛠️ Roadmap
- [ ] Implementación de Entidades Base.
- [ ] Sistema de Autenticación.
- [ ] CRUD de Clientes y Productos.
- [ ] Motor de Cotizaciones.
- [ ] Generación de PDFs.
- [ ] Pruebas Unitarias (>70% cobertura).

---

## 📄 Licencia
Este proyecto está bajo la Licencia MIT.

---
Desarrollado con ❤️ para la gestión comercial eficiente.
