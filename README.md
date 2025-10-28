# 🧾 README – Ciclo 4: Silk Road … with Advanced Robots! (Extensión de Tipos y Refactorización Final)

## 1. Descripción general

Este ciclo amplía el simulador **SilkRoad** integrando **nuevos tipos de robots y tiendas**, además de realizar una **refactorización completa** que mejora la estabilidad, la organización del código y la claridad del sistema.

El objetivo principal fue dotar al simulador de un comportamiento más versátil y realista, manteniendo la compatibilidad total con los ciclos anteriores.  
Se optimizó el flujo visual, se corrigieron errores estructurales y se añadieron nuevos comportamientos sin romper las funcionalidades existentes.

**Nuevas funcionalidades incluidas:**
- Tipos de tiendas: `normal`, `autonomous`, `fighter`.  
- Tipos de robots: `normal`, `neverback`, `tender`.  
- Refactor visual y estructural para mantener claridad y cohesión en el simulador.

---

## 2. Estructura del proyecto

- **SilkRoad.java** – Control central del simulador: gestiona robots, tiendas, ganancias, visualización y movimientos.  
- **Store.java** – Representa tiendas en la ruta, ahora con tipos (`normal`, `autonomous`, `fighter`) y comportamiento diferenciado.  
- **Robot.java** – Representa robots con nuevos modos de operación (`normal`, `neverback`, `tender`), registro de ganancias y movimiento.  
- **Spiral.java** – Conversión de posiciones a coordenadas visuales en espiral para el tablero.  
- **shapes (Canvas, Rectangle, Circle)** – Librería visual utilizada para la representación gráfica.  

---

## 3. Requisitos cumplidos

1. Crear y visualizar la ruta de la seda.  
2. Añadir y eliminar tiendas con control de tipo (`normal`, `autonomous`, `fighter`).  
3. Añadir y eliminar robots con tipo definido (`normal`, `neverback`, `tender`).  
4. Controlar el movimiento de robots, aplicando reglas especiales según tipo.  
5. Reabastecer tiendas y reflejar visualmente su estado (vacías en gris).  
6. Consultar tiendas vaciadas y ganancias por robot (`emptiedStores`, `profitPerMove`).  
7. Mostrar barra de progreso de ganancias y parpadeo del robot con mayor profit.  
8. Mantener una interfaz estable mediante refactorización visual (`redraw`, `drawStores`, `updateRobots`, `updateProfitBar`).  

---

## 4. Cómo ejecutar (BlueJ)

1️⃣ Abrir el proyecto en **BlueJ**.  
2️⃣ Asegurarse de que el paquete `shapes` esté disponible.  
3️⃣ Compilar las clases en este orden:  
   `Store.java` → `Robot.java` → `SilkRoad.java`.  

**Ejemplo de ejecución:**

```java
SilkRoad r = new SilkRoad(10);

// Crear tiendas
r.placeStore("normal", 2, 20);
r.placeStore("autonomous", 4, 50);
r.placeStore("fighter", 6, 30);

// Crear robots
r.placeRobot("normal", 1);
r.placeRobot("neverback", 3);
r.placeRobot("tender", 5);

// Mover robots
r.moveRobots();

// Consultar resultados
r.emptiedStores();
r.profitPerMove();
```

**Visualización:**  
- Ejecutar `r.makeVisible()` para activar el modo gráfico.  
- Tiendas se muestran como rectángulos, robots como círculos.  
- Tiendas vacías se vuelven grises y el robot más rentable parpadea.

---

## 5. Decisiones de diseño

- **Extensión flexible:** Se añadieron los tipos como atributos dentro de `Store` y `Robot`, en lugar de crear nuevas subclases, manteniendo compatibilidad con el código previo.  
- **Refactor estructural:** Se eliminaron duplicaciones y se unificaron métodos (`withdraw`, `updateAppearance`), mejorando la mantenibilidad.  
- **Preservación visual:** Se mantuvo la misma estética del simulador original, solo optimizando su rendimiento y claridad.  
- **Separación lógica:** `SilkRoad` se encarga de la lógica de simulación, mientras que `Store` y `Robot` definen comportamiento y estado individual.  

---

## 6. Pruebas

Se realizaron pruebas manuales exhaustivas en BlueJ:

- Verificación de tiendas `autonomous` con posiciones aleatorias.  
- Confirmación de que tiendas `fighter` solo pueden ser vaciadas por robots con mayor ganancia.  
- Validación de robots `neverback` (sin retroceso) y `tender` (recoge mitad de los tenges).  
- Ejecución de `moveRobots()` con distintos escenarios combinados.  
- Validación visual del parpadeo del robot más rentable.  

**Resultados:**  
El simulador compila correctamente, muestra el comportamiento esperado y refleja visualmente los estados sin errores de ejecución.

---

## 7. Validación manual sugerida

Ejecutar la simulación con distintos tipos de robots y tiendas, verificando:
1. Tiendas autónomas cambian de posición al crearse.  
2. Robots `tender` toman la mitad del dinero disponible.  
3. Robots `neverback` no retroceden posiciones previas.  
4. Tiendas `fighter` resisten robots con menos profit.  
5. Tiendas vacías aparecen grises.  
6. Barra de ganancias aumenta con los movimientos.  
7. Robot con mayor ganancia parpadea al final.  

---

## 8. Limitaciones y futuro

- **Herencia futura:** Se podría usar una jerarquía de clases (`FighterStore`, `TenderRobot`, etc.) para aislar comportamientos.  
- **Animación paso a paso:** Mejorar `simulate()` para mostrar día a día el progreso.  
- **Escalabilidad:** Optimizar estructuras si se amplía el número de tiendas o robots.  
- **Persistencia:** Exportar resultados (ganancias, movimientos) a archivos externos.  

---

## 9. Autores

**Camilo Aguirre**  
**Mateo Sánchez**  
Fecha: 28-10-2025
