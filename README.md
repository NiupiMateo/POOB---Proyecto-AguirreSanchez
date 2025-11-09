# 🧾 README – Ciclo 5: Silk Road … with Robots! (Cierre del Proyecto)

## 1. Descripción general  
El ciclo 5 representa la **etapa final del desarrollo del simulador SilkRoad**, en la cual se consolidó el proyecto integrando todas las funcionalidades creadas durante los ciclos anteriores, reforzando su estabilidad, modularidad y comportamiento visual.  

Durante esta fase se realizó la **integración completa del simulador en BlueJ**, con todas sus clases funcionales y de prueba, además de una revisión final de la arquitectura y la documentación.  
El objetivo fue dejar un producto final **estable, legible y completamente funcional**, capaz de simular el problema *The Silk Road… with Robots!* de forma visual e interactiva.

---

## 2. Objetivos del ciclo  
- Unificar todos los módulos (SilkRoad, Robot, Store, Spiral, SilkRoadContest) en una estructura coherente y funcional.  
- Ejecutar pruebas unitarias, colectivas y de aceptación para garantizar la correcta operación del sistema.  
- Revisar la arquitectura final y asegurar la correcta comunicación entre clases.  
- Documentar el sistema con base en la implementación final.  
- Presentar la simulación completa, validando las funcionalidades visuales y lógicas del proyecto.  

---

## 3. Estructura del proyecto  
El proyecto se compone de los siguientes módulos:

- **SilkRoad.java** – Controlador principal de la simulación. Administra robots, tiendas, ganancias, visualización y movimientos.  
- **Store.java** – Define las tiendas con distintos tipos (`normal`, `autonomous`, `fighter`, `trap`), manejando su dinero y estado visual.  
- **Robot.java** – Representa robots (`normal`, `neverback`, `tender`, `dummy`) con comportamiento y ganancias individuales.  
- **Spiral.java** – Calcula las coordenadas (x, y) para ubicar elementos en espiral dentro del tablero visual.  
- **SilkRoadContest.java** – Controla la parte de concurso y resolución de casos de la maratón (solve y simulate).  
- **SilkRoadException.java** – Maneja los errores personalizados del simulador.  
- **shapes (Canvas, Rectangle, Circle)** – Librería visual que permite representar gráficamente los elementos.  

### Clases de prueba:
- **SilkRoadC4Test / SilkRoadCC4Test** – Pruebas unitarias y colectivas del simulador.  
- **SilkRoadContestTest / SilkRoadContestCTest** – Pruebas específicas del módulo de concurso.  
- **SilkRoadATest** – Pruebas de aceptación con verificación visual e interacción del usuario.  

---

## 4. Requisitos cumplidos  

### 🔧 Funcionales
- Creación de la ruta de la seda con longitud variable.  
- Adición y eliminación de tiendas y robots en cualquier posición válida.  
- Implementación de tipos especiales de tiendas y robots con reglas personalizadas:  
  - *Autonomous stores* se ubican automáticamente.  
  - *Fighter stores* solo entregan dinero a robots con mayor ganancia.  
  - *Trap stores* hacen perder dinero al robot visitante.  
  - *Neverback robots* no pueden retroceder.  
  - *Tender robots* solo recogen la mitad de los tenges.  
- Reabastecimiento general de tiendas (`resupplyStores()`).  
- Reinicio completo de simulación (`reboot()`).  
- Consultas de estado (`emptiedStores()`, `profitPerMove()`).  
- Control visual completo: tiendas, robots, barra de ganancias y parpadeo del robot con mayor profit.  

### 🧱 De diseño
- Arquitectura modular compuesta por las clases principales (`SilkRoad`, `Robot`, `Store`, `Spiral`).  
- Separación clara de responsabilidades:  
  - Lógica → `SilkRoad`  
  - Modelos → `Store`, `Robot`  
  - Visualización → `Spiral` + `shapes`  
- Diagrama de clases completamente integrado (ver estructura de BlueJ).  
- Eliminación de redundancias y refactorización para mayor legibilidad.  

### 🤞 De pruebas
- Pruebas unitarias y colectivas validadas con resultados esperados.  
- Pruebas de aceptación visual (`SilkRoadATest`) que permiten validar la simulación directamente en BlueJ, con confirmación del usuario.  
- Todos los métodos principales y constructores fueron verificados de forma manual y visual.  

---

## 5. Ejecución del proyecto (BlueJ)
1. Abrir el proyecto en **BlueJ**.  
2. Asegurar que el paquete `shapes` esté disponible.  
3. Compilar las clases en este orden:  
   `Store.java → Robot.java → Spiral.java → SilkRoad.java → SilkRoadContest.java`  
4. Crear un objeto de tipo `SilkRoad` y ejecutar los métodos del simulador.  

### Ejemplo:
```java
SilkRoad r = new SilkRoad(10);
r.makeVisible();
r.placeStore("fighter", 6, 50);
r.placeStore("trap", 3, 40);
r.placeRobot("tender", 2);
r.placeRobot("neverback", 4);
r.moveRobots();
r.profitPerMove();
```

**Resultado esperado:**  
- El robot *tender* recolecta la mitad del dinero.  
- El *neverback* se mueve sin retroceder.  
- Las tiendas se actualizan visualmente (gris = vacía).  
- La barra verde muestra las ganancias acumuladas.  
- El robot con mayor ganancia parpadea al finalizar.  

---

## 6. Pruebas de aceptación (SilkRoadATest)
Las pruebas de aceptación finales fueron diseñadas para observar el comportamiento real del simulador.  
Cada prueba muestra el tablero en pantalla y solicita al usuario validar si el resultado visual es correcto.

**Escenarios incluidos:**
1. *Tienda fighter y robot tender* — verificación de ganancia parcial.  
2. *Robot neverback y tienda autónoma* — validación de movimiento restringido.  
3. *Combinación de tiendas trap y fighter* — simulación de pérdidas y resistencias.  

---

## 7. Validación manual sugerida
Durante la sustentación, se recomienda mostrar:
- Cómo se construye la espiral y cómo se ubican las tiendas/robots.  
- Diferencias entre robots y tiendas según su tipo.  
- Ejecución de `moveRobots()` y `reboot()`.  
- Cambio visual de las tiendas (gris al vaciarse).  
- Parpadeo del robot con mayor ganancia.  
- Confirmación visual en pruebas de aceptación.  

---

## 8. Retrospectiva del ciclo final
**Logros principales:**  
- Consolidación completa del simulador funcional.  
- Integración de todos los tipos y comportamientos.  
- Corrección de errores visuales y lógicos.  
- Implementación de pruebas completas (unitarias, colectivas y de aceptación).  

**Aprendizajes:**  
- Importancia de la modularidad y la refactorización.  
- Validación continua de la interfaz visual.  
- Trabajo colaborativo constante para mantener coherencia entre módulos.  

**Posibles mejoras futuras:**  
- Agregar persistencia (guardar y cargar simulaciones).  
- Mejorar animaciones y control paso a paso.  
- Extender con interfaz gráfica independiente.  

---

## 9. Autores
👤 **Camilo Aguirre**  
👤 **Mateo Sánchez**  
🕛 *Fecha de entrega:* 08 de noviembre de 2025  
🏢 *Escuela Colombiana de Ingeniería Julio Garavito*  
📚 Proyecto Final: *The Silk Road … with Robots!*

