# **Scrum aplicado a BeeLine** 

 **PO + SM + Dev** Único, Scrum ligero para una sola persona.

---

## **Pre-Sprint 0: Preparación y Product Backlog Inicial (Día 1 - 3)**

**Actividad principal:**

* Definir alcance del MVP.
* Crear repositorio GitHub y configurar CMake, GitHub Actions (compilación/pruebas), Issues y Projects.
* Esbozar arquitectura:

  * Módulo de entrada/salida CSV.
  * Módulo de algoritmos.
  * CLI.

**Product Backlog inicial (priotizado)**:

1. **HU1**: Como usuario, quiero ejecutar BeeLine desde terminal con parámetros de entrada/salida.
2. **HU2**: Como usuario, quiero leer datos desde CSV de nodos/aristas.
3. **HU3**: Como usuario, quiero resolver el problema de ruta más corta usando Dijkstra.
4. **HU4**: Como usuario, quiero resolver el problema de árbol mínimo usando Kruskal.
5. **HU5**: Como usuario, quiero recibir un CSV con los resultados.
6. **HU6**: Como usuario, quiero ver una barra de progreso y mensajes en color.
7. **HU7**: Como desarrollador, quiero tener pruebas unitarias para validar los algoritmos.
8. **HU8**: Como docente, quiero un modo "verbose" para mostrar pasos del algoritmo.

---

## **Sprint 1 (2 semanas)**

**Objetivo del sprint**: BeeLine ejecuta Dijkstra y Kruskal con entrada/salida en CSV.
**Historias seleccionadas**: HU1, HU2, HU3, HU4, HU5.
**Entregable**: Versión v0.1 funcional, sin modo verbose.

---

## **Sprint 2 (2 semanas)**

**Objetivo**: Mejorar experiencia y preparar para contribuciones.
**Historias seleccionadas**: HU6, HU7, HU8.
**Entregable**: v0.2 con colores, barra de progreso y modo educativo.

---

## **Herramientas de seguimiento**

* **GitHub Projects**: Kanban (To do / In progress / Done).
* **GitHub Issues**: Cada HU como issue, con etiquetas.
* **GitHub Releases**: Publicar binarios de cada sprint.

---

# **Product Backlog – BeeLine** 🐝

---

## **HU1 – Ejecución desde terminal**

**Historia de Usuario:**
Como usuario, quiero ejecutar BeeLine desde la terminal con parámetros de entrada y salida para resolver un problema específico.

**Criterios de aceptación:**

* BeeLine acepta parámetros como:

  ```bash
  beeline input.csv output.csv --algoritmo dijkstra --origen A
  ```
* Si los parámetros son inválidos, muestra mensaje de ayuda.
* Soporta `--help` para mostrar comandos disponibles.

**Tareas técnicas:**

* Configurar parser de argumentos (ej. `getopt` o `cxxopts`).
* Implementar comando `--help`.
* Validar rutas y existencia de archivos.

---

## **HU2 – Lectura de CSV**

**Historia de Usuario:**
Como usuario, quiero que BeeLine lea datos de un archivo CSV que contenga nodos y aristas para que el programa pueda procesarlos.

**Criterios de aceptación:**

* Soporta CSV con encabezados `origen, destino, peso`.
* Detecta errores de formato y muestra advertencia.
* Soporta separador `,` y `;`.

**Tareas técnicas:**

* Implementar función `leerCSV()`.
* Validar formato y datos numéricos.
* Escribir pruebas unitarias para casos válidos y con errores.

---

## **HU3 – Algoritmo Dijkstra**

**Historia de Usuario:**
Como usuario, quiero calcular la ruta más corta entre un nodo origen y todos los demás usando Dijkstra.

**Criterios de aceptación:**

* Devuelve distancias mínimas desde el nodo origen.
* Si un nodo es inalcanzable, marcar como `INF`.
* Procesa grafos no dirigidos y dirigidos.

**Tareas técnicas:**

* Implementar módulo `dijkstra.cpp`.
* Optimizar con cola de prioridad.
* Pruebas unitarias con grafos de ejemplo.

---

## **HU4 – Algoritmo Kruskal**

**Historia de Usuario:**
Como usuario, quiero calcular el árbol de expansión mínima usando Kruskal.

**Criterios de aceptación:**

* Devuelve lista de aristas del MST y peso total.
* Funciona en grafos no dirigidos.
* Si el grafo no es conexo, devuelve MST por componente.

**Tareas técnicas:**

* Implementar módulo `kruskal.cpp` con Union-Find.
* Validar casos de grafos pequeños y grandes.
* Escribir pruebas unitarias.

---

## **HU5 – Escritura de CSV de resultados**

**Historia de Usuario:**
Como usuario, quiero que BeeLine exporte los resultados a un archivo CSV para poder procesarlos en otras herramientas.

**Criterios de aceptación:**

* Soporta encabezados claros (`nodo, distancia` o `origen, destino, peso`).
* Genera archivo nuevo sin sobrescribir sin confirmación.
* Maneja errores de permisos o disco lleno.

**Tareas técnicas:**

* Implementar función `escribirCSV()`.
* Pruebas unitarias con distintos tamaños de salida.
* Validar codificación UTF-8.

---

## **HU6 – Barra de progreso y colores**

**Historia de Usuario:**
Como usuario, quiero ver una barra de progreso y mensajes en colores para entender el avance.

**Criterios de aceptación:**

* Barra de progreso en porcentaje.
* Colores para advertencias, errores y resultados.
* Compatible con terminales comunes.

**Tareas técnicas:**

* Usar librería como `termcolor` o ANSI codes.
* Implementar barra en funciones largas.
* Pruebas en Windows y Linux.

---

## **HU7 – Pruebas unitarias**

**Historia de Usuario:**
Como desarrollador, quiero tener pruebas unitarias para garantizar que los algoritmos funcionan correctamente.

**Criterios de aceptación:**

* Pruebas para Dijkstra y Kruskal.
* Pruebas para entrada/salida CSV.
* Integración en CI/CD de GitHub Actions.

**Tareas técnicas:**

* Configurar `Catch2` o `GoogleTest`.
* Crear dataset de prueba.
* Integrar pruebas en workflow.

---

## **HU8 – Modo verbose educativo**

**Historia de Usuario:**
Como docente, quiero un modo `--verbose` que muestre paso a paso la ejecución de los algoritmos.

**Criterios de aceptación:**

* Muestra en consola cada iteración del algoritmo.
* Colores para resaltar cambios.
* Se activa con `--verbose`.

**Tareas técnicas:**

* Agregar logs detallados.
* Opcional: ralentizar pasos para visualización.
* Pruebas con ejemplos educativos.

---

## **HU9 – Documentación inicial**

**Historia de Usuario:**
Como usuario, quiero contar con una guía rápida para usar BeeLine.

**Criterios de aceptación:**

* README con ejemplos.
* Instrucciones de compilación e instalación.
* Tabla de algoritmos soportados.

**Tareas técnicas:**

* Escribir README.md.
* Crear ejemplos en carpeta `/examples`.
* Capturas de pantalla de ejecución.

---

```
Título,Descripción,Etiqueta,Prioridad
HU1 – Ejecución desde terminal,"Como usuario, quiero ejecutar BeeLine desde la terminal con parámetros de entrada y salida para resolver un problema específico.",Sprint 1,Alta
HU2 – Lectura de CSV,"Como usuario, quiero que BeeLine lea datos de un archivo CSV que contenga nodos y aristas para que el programa pueda procesarlos.",Sprint 1,Alta
HU3 – Algoritmo Dijkstra,"Como usuario, quiero calcular la ruta más corta entre un nodo origen y todos los demás usando Dijkstra.",Sprint 1,Alta
HU4 – Algoritmo Kruskal,"Como usuario, quiero calcular el árbol de expansión mínima usando Kruskal.",Sprint 2,Alta
HU5 – Escritura de CSV de resultados,"Como usuario, quiero que BeeLine exporte los resultados a un archivo CSV para poder procesarlos en otras herramientas.",Sprint 1,Media
HU6 – Barra de progreso y colores,"Como usuario, quiero ver una barra de progreso y mensajes en colores para entender el avance.",Sprint 2,Media
HU7 – Pruebas unitarias,"Como desarrollador, quiero tener pruebas unitarias para garantizar que los algoritmos funcionan correctamente.",Sprint 1,Alta
HU8 – Modo verbose educativo,"Como docente, quiero un modo --verbose que muestre paso a paso la ejecución de los algoritmos.",Sprint 2,Media
HU9 – Documentación inicial,"Como usuario, quiero contar con una guía rápida para usar BeeLine.",Sprint 1,Media
```