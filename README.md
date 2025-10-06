# README – Ciclo 3: Silk Road … with Robots! (Simulación y Concurso)

## 1. Descripción general
Este ciclo extiende el simulador **SilkRoad** para **resolver** y **simular** el problema ICPC 2024 *The Silk Road … with Robots!*.

- **Requisito 14 – Resolver**: Con `SilkRoadContest.solve(int[][] days)` se calcula la **ganancia máxima acumulada** tras cada día, aplicando la utilidad `tenges - distancia` y sumando solo valores positivos.
- **Requisito 15 – Simular**: Con `SilkRoadContest.simulate(int[][] days, boolean slow)` se muestra la solución en el tablero visual, con control de velocidad (`slow`).

La lógica de concurso queda separada del tablero para mejorar claridad y extensibilidad.

---

## 2. Estructura del proyecto
- `SilkRoad.java` – Motor visual (estado de tiendas/robots, dibujo, barra de ganancia, movimientos).
- `Robot.java` – Modelo de robot (ubicaciones, color, ganancias por movimiento y total, figura `Circle`).
- `Store.java` – Modelo de tienda (ubicación, tenges, veces vaciada, apariencia, figura `Rectangle`).
- `SilkRoadContest.java` – Capa de concurso (resuelve con `solve`, simula con `simulate`).
- `Spiral.java` – Conversión de índice a coordenadas de espiral para dibujar en el canvas.
- **Pruebas**:
  - `SilkRoadContestTest.java` – 6 pruebas unitarias (3 positivas, 3 negativas) en modo silencioso.
  - `SilkRoadContestCTest.java` – Casos colectivos con convención `accordingASShould...`.

Dependencias visuales: paquete `shapes` (Canvas, Rectangle, Circle).

---

## 3. Requisitos cumplidos
- **10.** Crear ruta desde entrada del concurso: `SilkRoad(int[][] days)`.
- **11.** Mover robots maximizando ganancia: `moveRobots()`.
- **12.** Consultas de estado: `emptiedStores()`, `profitPerMove()`.
- **Usabilidad:** Tiendas vacías grises (`Store.updateAppearance()`), parpadeo del robot top (`SilkRoad.blinkTopRobot()`).
- **14.** Resolver la maratón: `SilkRoadContest.solve(...)`.
- **15.** Simular la solución: `SilkRoadContest.simulate(..., slow)`.

---

## 4. Cómo ejecutar (BlueJ)
1. Abrir el proyecto en BlueJ y compilar todo.
2. Asegurar que `shapes` esté disponible (Canvas/Rectangle/Circle).
3. En el terminal de objetos:
   - **Resolver**:
     ```java
     int[][] days = { {1,20}, {2,15,15}, {2,40,50}, {1,50}, {2,80,20}, {2,70,30} };
     SilkRoadContest c = new SilkRoadContest();
     int[] r = c.solve(days);
     ```
   - **Simular** (lento):
     ```java
     c.simulate(days, true);
     ```
   - **Simular** (rápido):
     ```java
     c.simulate(days, false);
     ```

---

## 5. Decisiones de diseño
- **Separación de responsabilidades:** concurso (`SilkRoadContest`) vs. tablero (`SilkRoad`).
- **Algoritmo sencillo y claro:** por tienda se toma la mejor utilidad positiva frente a cualquier robot.
- **Interfaz y feedback:** barra de progreso verde, tiendas vacías grises, parpadeo del robot con mayor ganancia.
- **Refactor de dibujo:** `redraw()` modularizado en `hideAllViews`, `drawStores`, `drawRobots` para legibilidad.

---

## 6. Pruebas
- **Unitarias (silenciosas)** en `SilkRoadContestTest.java`:
  - `testSolve_EmptyDays_ReturnsEmptyArray`
  - `testSolve_SamePosRobotStore_PositiveProfit`
  - `testSolve_ICPCLikeSequence_Cumulative`
  - `testSolve_NullDays_ThrowsNPE`
  - `testSolve_Type2MissingCoins_ThrowsAIOOBE`
  - `testSimulate_NullDays_ThrowsNPE`
- **Colectivas (AS)** en `SilkRoadContestCTest.java`:
  - `accordingASShouldAccumulateProfitsPerDay`
  - `accordingASShouldReturnZeroWhenOnlyRobotsOrOnlyStores`
  - `accordingASShouldThrowWhenType2LacksCoins`
  - `accordingASShouldThrowOnNullDaysInput`

---

## 7. Validación manual sugerida
- Ejecutar `simulate(days, true)` y verificar visualmente:
  - Posición de tiendas/robots en la espiral.
  - Tiendas vacías en gris tras visitas.
  - Parpadeo del robot con mayor ganancia.
  - Barra de progreso coherente con `profit()`.
- Consultar:
  - `emptiedStores()` → posiciones y conteo.
  - `profitPerMove()` → matriz de ganancias por robot.

---

## 8. Limitaciones y futuro
- **Escalabilidad:** para instancias masivas (n≈2e5) se requerirían estructuras avanzadas (fuera del alcance académico actual).
- **Simulación paso a paso:** posible mejora para animar por día y registrar logs visuales.

---

## 9. Autores
- Camilo Aguirre
- Mateo Sánchez

**Fecha:** 05-10-2025
