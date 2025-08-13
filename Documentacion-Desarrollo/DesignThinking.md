# **Design Thinking aplicado a EnRuta**

## **1. Descubrimiento / Empatía / Investigación (Divergencia)**

* **Contexto detectado**:  
  En muchas ciudades, como en nuestro caso, los usuarios del transporte público utilizan grupos de WhatsApp para informar en tiempo real la ubicación aproximada de los autobuses.  
  Actualmente:
  * La información es valiosa pero está dispersa en chats y no se centraliza.
  * No existe un sistema público y gratuito que organice y visualice estos datos en tiempo real.
  * La información puede estar escrita con variaciones, errores ortográficos o en formatos no estandarizados.

* **Necesidades de los usuarios**:
  * Pasajeros que quieren saber dónde está el próximo autobús de su ruta.
  * Conductores y administradores de rutas que desean conocer la ubicación y frecuencia del servicio.
  * Comunidad y desarrolladores que podrían crear soluciones a partir de estos datos abiertos.

* **Hallazgos clave**:
  * Los datos ya existen y se actualizan constantemente gracias a la comunidad.
  * No se requiere instalar dispositivos GPS en cada unidad, solo aprovechar la información colaborativa.
  * La principal barrera es la **limpieza, estructuración y acceso** a los datos.

---

## **2. Definición / Síntesis (Divergencia)**

* **Problema a resolver**:  
  *"La información sobre la ubicación de los autobuses urbanos está disponible en grupos de WhatsApp pero no está centralizada, estandarizada ni es fácilmente accesible para la comunidad en general."*

* **Oportunidad de impacto**:
  * Facilitar el acceso a información confiable y en tiempo real sobre transporte público.
  * Empoderar a la comunidad y reducir la incertidumbre sobre tiempos de espera.
  * Aprovechar una fuente de datos ya existente para fines de análisis, planificación urbana y desarrollo de aplicaciones.

---

## **3. Ideación (Divergencia y Convergencia)**

* **Lluvia de ideas de funciones iniciales**:
  * Script para extraer mensajes de grupos de WhatsApp (usando API oficial o técnicas de exportación).
  * Procesamiento de texto para estandarizar información (NLP básico, regex).
  * Base de datos centralizada con fecha, hora, número de unidad, ubicación y destino.
  * Dashboard web para visualizar la ubicación aproximada de autobuses en un mapa.
  * API pública para que otros desarrolladores creen herramientas.
  * Bot de consulta (Telegram/WhatsApp) para preguntar por el estado de una ruta.

* **Selección para primera versión (Fase 1)**:
  * Extracción y limpieza de datos desde mensajes exportados.
  * Almacenamiento en una base de datos (MySQL, PostgreSQL).
  * Documentación clara para que otros puedan replicar el proceso.

---

## **4. Implementación / Construcción (Divergencia y Convergencia)**

* **Primera iteración (v0.1)**:
  * Script que lee mensajes exportados de WhatsApp en formato `.txt`.
  * Limpieza y normalización de datos: separar número de autobús, ubicación y destino.
  * Guardado de datos en base de datos con timestamp.

* **Pruebas y feedback**:
  * Validar con un grupo pequeño de usuarios que los datos procesados correspondan a la realidad.
  * Ajustar expresiones regulares y diccionarios de sinónimos/errores ortográficos.

* **Iteraciones siguientes**:
  * Integrar visualización en mapa en tiempo real.
  * Implementar consulta por API o bot.
  * Habilitar sistema de contribución para que la comunidad envíe datos desde distintas fuentes.
