# 🍎 Urban.Grocers API Testing - New Functionalities
**QA Engineer:** Daniel Chacon | **Location:** Chile 🇨🇱

Este proyecto consiste en el análisis de requisitos y la ejecución de pruebas de caja negra (Black Box Testing) sobre la versión actualizada de la API de **Urban.Grocers**. El foco principal fue validar la lógica de negocio de los kits de productos y el sistema de cálculo de delivery "Order and Go".

## 🎯 Alcance del Proyecto
* **Módulo de Kits:** Validación del endpoint `POST /api/v1/kits/{id}/products`.
* **Módulo de Delivery:** Verificación de disponibilidad y costos en `POST /order-and-go/v1/delivery`.
* **Documentación Técnica:** Uso de **Apidoc** para la interpretación de contratos de API y requisitos de backend.

## 🛠️ Tecnologías y Herramientas
* **Postman:** Ejecución de requests, validación de Status Codes y scripts de prueba automáticos.
* **Jira:** Gestión, priorización y reporte de defectos (Bugs).
* **Google Sheets:** Diseño de listas de comprobación (Checklists) y casos de prueba detallados.
* **JSON:** Manipulación de estructuras de datos para los cuerpos de solicitud (Body).

## 🧠 Retos Técnicos y Soluciones (Engineering Mindset)

| Escenario de Prueba | Estrategia de Resolución |
| :--- | :--- |
| **Límite de Productos (Boundary Value):** El requisito indica un máximo de 30 productos por kit. | Se aplicó la técnica de **Valores Límite** (29, 30 y 31 productos) para confirmar que el backend maneja el error `400 Bad Request` correctamente al exceder el límite. |
| **Automatización de Validaciones:** Necesidad de verificar respuestas de forma ágil y repetible. | Implementación de **Scripts en la pestaña Tests** de Postman para validar automáticamente el Status Code, el tiempo de respuesta (<500ms) y la estructura del JSON. |
| **Mantenibilidad de la Suite:** La URL del contenedor de la API cambia frecuentemente en el entorno de pruebas. | Uso de **Variables de Colección** (`{{baseUrl}}`) para parametrizar los endpoints, permitiendo que la suite sea portátil y fácil de actualizar con un solo clic. |
| **Lógica de Negocio en Delivery:** Validar costos variables según el servicio "Order and Go". | Pruebas de **Partición de Equivalencia** para asegurar que el cálculo de precio de entrega coincida con las reglas de negocio definidas en la documentación. |



## 📊 Resumen Ejecutivo de Resultados
Tras la ejecución de la suite de pruebas completa, estos son los hallazgos principales para el equipo de desarrollo:

* **Casos de Prueba Diseñados:** 15
* **Ejecuciones Exitosas (Passed):** 11
* **Fallos Detectados (Failed):** 4
* **Estado de la Entrega:** **RIESGO MODERADO**. Se encontraron discrepancias en la validación de límites de los kits que requieren corrección antes del despliegue.

## 🐛 Gestión de Defectos (Bugs)
Se reportaron errores en Jira con foco en la experiencia de usuario y estabilidad del sistema:
1. **Fallo en Límite Superior:** La API permitía agregar más de 30 productos bajo ciertas condiciones de duplicidad.
2. **Mensajes de Error Inconsistentes:** El sistema devolvía errores de servidor (500) en lugar de errores de validación de cliente (400) al usar IDs inexistentes.

## 🚀 Cómo revisar este proyecto
1. **Checklist:** Puedes ver el diseño de mis pruebas en este [Enlace a mi Google Sheets] (Configurado como Comentador).
2. **Colección de Postman:** Importa el archivo `UrbanGrocers_API_Tests.json` incluido en este repositorio.
3. **Variables:** Asegúrate de configurar la variable `baseUrl` en tu entorno de Postman con la URL activa del servidor.
