# **Lean Startup aplicado a EnRuta**

## **1. Hipótesis**

* **Hipótesis de problema**:  
  Los usuarios del transporte público desean conocer la ubicación y destino de los autobuses en tiempo real, pero la información disponible en grupos de WhatsApp está desorganizada, es difícil de filtrar y no está centralizada.

* **Hipótesis de solución**:  
  Un sistema que extraiga, limpie y almacene automáticamente los mensajes de ubicación de autobuses desde grupos de WhatsApp, y los presente en una base de datos estructurada, permitirá construir herramientas útiles para usuarios y desarrolladores. Esto incentivará la adopción y el aporte de la comunidad.

---

## **2. Producto Mínimo Viable (MVP)**

* **Funcionalidad mínima**:

  1. Importar mensajes exportados de WhatsApp en formato `.txt`.
  2. Detectar automáticamente número de autobús, ubicación y destino usando expresiones regulares y limpieza de texto.
  3. Guardar registros limpios en una base de datos (SQLite o PostgreSQL) con fecha y hora.
  
* **Experiencia mínima**:
  
  * Ejecutar un solo comando para procesar y guardar datos:

    ```bash
    enruta datos_chat.txt --db enruta.db
    ```
  * Mostrar un resumen en terminal con:
    - Total de mensajes procesados.
    - Mensajes válidos y descartados.
    - Rutas detectadas.
  
---

## **3. Métricas de Éxito (MVP)**

* **Cuantitativas**:
  * Número de mensajes procesados por día.
  * Porcentaje de mensajes limpios frente a mensajes totales.
  * Cantidad de rutas y unidades identificadas.
  * Usuarios o desarrolladores que consultan la base de datos.

* **Cualitativas**:
  * Feedback de usuarios sobre la precisión de los datos.
  * Interés de desarrolladores para usar la base en sus proyectos.
  * Solicitudes de nuevas funcionalidades (bot, dashboard, API).

---

## **4. Ciclo de Validación**

1. **Construir** → Crear script que importe, limpie y guarde datos de un chat exportado.
2. **Medir** → Probar con grupos reales de WhatsApp de rutas de la ciudad y evaluar precisión.
3. **Aprender** → Ajustar reglas de extracción, mejorar manejo de errores ortográficos y ampliar compatibilidad con distintos formatos de mensajes.
