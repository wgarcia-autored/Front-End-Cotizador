# Cotizador AD BOMESCO 🚀
Front-end y documentación de la herramienta automatizada de cotizaciones.

## 1. Ubicación de la Información y Repositorios
* **Base de Datos:** Supabase (Nube - PostgreSQL) | Almacena productos, cotizaciones y usuarios.
* **Almacenamiento de Archivos:** Supabase Storage (Nube - Bucket público) | Aloja plantillas HTML y recursos gráficos.
* **Backend:** n8n (Migrando a la nube) | Orquestación de lógica de negocio, webhooks y procesos ETL.
* **Frontend:** Vercel (Nube) | Interfaz gráfica de usuario desplegada en producción.

## 2. Estructura de Carpetas (Origen Local)
```text
C:\
├── n8n_shared\
│   ├── inventario.xlsx          # Sincronizado desde Odoo
│   ├── plantillas\              # Respaldos HTML (cotización, carátula, presentación)
│   └── logs\                    # Registro de sincronizaciones locales
└── frontend-cotizador\          # Código fuente del Frontend
```

## 3. Esquema de Base de Datos (Supabase)
### Tablas Principales
* `products`: Base de datos de productos (PK: `reference_internal`).
* `quotations`: Historial de cotizaciones emitidas.
* `product_assets`: Enlaces a imágenes y fichas técnicas.
* `authorized_phones`: Números validados para integraciones de mensajería.

### Buckets de Storage
* `templates`: Código base de documentos imprimibles.
* `assets`: Identidad gráfica de la empresa.

## 4. Endpoints de n8n Activos
* `GET /webhook/all-products` | Envía el catálogo consolidado completo con filtros precalculados.
* `POST /webhook/search-products` | Ejecuta búsquedas parciales rápidas por coincidencia de texto.
* `POST /webhook/simple-cotizacion` | Procesa el JSON del carrito y devuelve la estructura HTML construida.
