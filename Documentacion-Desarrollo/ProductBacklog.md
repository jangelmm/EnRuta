# **Product Backlog – EnRuta**

---

## Historias de Usuario

---

### **HU1 – Recepción de mensajes desde WhatsApp Cloud API**

**Historia de Usuario:**
Como desarrollador, quiero recibir mensajes enviados al número de WhatsApp de EnRuta a través de un webhook para poder procesarlos automáticamente.

**Criterios de aceptación:**

* El sistema recibe mensajes en formato texto.
* Si el mensaje no tiene contenido válido, se descarta con un log.
* El endpoint responde con código HTTP 200 para confirmar la recepción a Meta.

**Tareas técnicas:**

* Configurar webhook con WhatsApp Cloud API.
* Implementar endpoint en **Python** con **Flask** o **FastAPI** para recibir POST.
* Guardar mensaje crudo en log temporal.

---

### **HU2 – Limpieza y normalización de texto**

**Historia de Usuario:**
Como desarrollador, quiero limpiar y normalizar el contenido de los mensajes para manejar errores ortográficos y formatos distintos.

**Criterios de aceptación:**

* Elimina caracteres especiales no necesarios.
* Detecta patrón “\<número> en \<lugar> para \<destino>” aunque tenga variaciones de mayúsculas o errores menores.
* Convierte a minúsculas y elimina espacios extra.

**Tareas técnicas:**

* Crear módulo `data_cleaner.py`.
* Implementar regex flexible para extraer número, ubicación y destino.
* Escribir pruebas unitarias con `pytest` para casos correctos y con errores.

---

### **HU3 – Almacenamiento en base de datos**

**Historia de Usuario:**
Como desarrollador, quiero guardar los mensajes procesados en una base de datos con fecha, remitente y contenido limpio para usarlos posteriormente.

**Criterios de aceptación:**

* Se almacena: fecha, remitente, ruta detectada, ubicación, destino.
* Evita registros duplicados si son el mismo mensaje en corto intervalo.
* Soporta PostgreSQL o SQLite para desarrollo rápido.

**Tareas técnicas:**

* Crear esquema en base de datos con **SQLAlchemy**.
* Implementar módulo `db_service.py` para inserción y consulta.
* Pruebas de conexión y guardado.

---

### **HU4 – Visualización en consola (modo debug)**

**Historia de Usuario:**
Como usuario técnico, quiero ver en la consola cada mensaje procesado para verificar que se está limpiando y guardando correctamente.

**Criterios de aceptación:**

* Muestra datos extraídos en formato legible.
* Incluye timestamp y remitente.
* Colores para resaltar errores o campos vacíos.

**Tareas técnicas:**

* Implementar logging con `logging` y `colorama`.
* Configurar logs por niveles (info, warn, error).

---

### **HU5 – Exportación de datos**

**Historia de Usuario:**
Como administrador, quiero exportar mensajes procesados a CSV o JSON para analizarlos externamente.

**Criterios de aceptación:**

* Soporta exportación de rango de fechas.
* Encabezados claros: `fecha, remitente, ruta, ubicación, destino`.
* Archivo descargable o guardado en carpeta local.

**Tareas técnicas:**

* Implementar función `exportar_datos()` en `db_service.py`.
* Validar formato y codificación UTF-8.
* Pruebas con datos pequeños y grandes.

---

### **HU6 – Respuesta automática opcional**

**Historia de Usuario:**
Como usuario que envía un mensaje, quiero recibir una confirmación automática de que mi reporte fue recibido.

**Criterios de aceptación:**

* Mensaje de agradecimiento con hora de recepción.
* Opcional (configurable en `.env`).
* No responde a mensajes vacíos o inválidos.

**Tareas técnicas:**

* Integrar envío de mensaje con WhatsApp Cloud API usando `requests`.
* Configuración para activar/desactivar respuesta.

---

### **HU7 – Configuración mediante variables de entorno**

**Historia de Usuario:**
Como desarrollador, quiero configurar credenciales y parámetros en un archivo `.env` para evitar exponer datos sensibles en el código.

**Criterios de aceptación:**

* Variables: token API, URL webhook, conexión DB, opciones de respuesta automática.
* El sistema lee y valida las variables al iniciar.

**Tareas técnicas:**

* Usar `python-dotenv` para carga de variables.
* Implementar validación de configuración en arranque.

---

### **HU8 – Pruebas unitarias**

**Historia de Usuario:**
Como desarrollador, quiero pruebas unitarias para asegurar que la limpieza, almacenamiento y exportación funcionan correctamente.

**Criterios de aceptación:**

* Pruebas para `data_cleaner`, `db_service` y exportación.
* Cobertura mínima del 80%.
* Integración con GitHub Actions.

**Tareas técnicas:**

* Configurar `pytest` y `coverage`.
* Crear dataset de prueba.
* Integrar con CI/CD.

---

## Tabla Resumen (CSV)

```
Título,Descripción,Etiqueta,Prioridad
HU1 – Recepción de mensajes desde WhatsApp Cloud API,"Como desarrollador, quiero recibir mensajes enviados al número de WhatsApp de EnRuta a través de un webhook para poder procesarlos automáticamente.",Sprint 1,Alta
HU2 – Limpieza y normalización de texto,"Como desarrollador, quiero limpiar y normalizar el contenido de los mensajes para manejar errores ortográficos y formatos distintos.",Sprint 1,Alta
HU3 – Almacenamiento en base de datos,"Como desarrollador, quiero guardar los mensajes procesados en una base de datos con fecha, remitente y contenido limpio para usarlos posteriormente.",Sprint 1,Alta
HU4 – Visualización en consola (modo debug),"Como usuario técnico, quiero ver en la consola cada mensaje procesado para verificar que se está limpiando y guardando correctamente.",Sprint 1,Media
HU5 – Exportación de datos,"Como administrador, quiero exportar mensajes procesados a CSV o JSON para analizarlos externamente.",Sprint 2,Media
HU6 – Respuesta automática opcional,"Como usuario que envía un mensaje, quiero recibir una confirmación automática de que mi reporte fue recibido.",Sprint 2,Media
HU7 – Configuración mediante variables de entorno,"Como desarrollador, quiero configurar credenciales y parámetros en un archivo .env para evitar exponer datos sensibles en el código.",Sprint 1,Alta
HU8 – Pruebas unitarias,"Como desarrollador, quiero pruebas unitarias para asegurar que la limpieza, almacenamiento y exportación funcionan correctamente.",Sprint 1,Alta
```

---

## Historias Épicas

---

### **E1 - Adquisición y procesamiento de datos**

Como desarrollador, quiero un sistema capaz de recibir, limpiar y almacenar mensajes de rutas de autobús enviados por WhatsApp para luego analizarlos.
Incluye: **HU1 – HU4 – HU7**

---

### **E2 - Distribución y análisis**

Como usuario o administrador, quiero herramientas para exportar datos, generar respuestas automáticas y garantizar calidad mediante pruebas, para aprovechar la información colectada.
Incluye: **HU5 – HU6 – HU8**
