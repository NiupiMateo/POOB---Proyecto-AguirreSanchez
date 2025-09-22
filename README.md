# Proyecto Inicial – Ciclos 1 y 2 (2025-2)

**Asignatura:** Desarrollo Orientado por Objetos (DOPO – POOB)  
**Institución:** Escuela Colombiana de Ingeniería Julio Garavito  

---

## 📌 Descripción

Este proyecto corresponde a los **Ciclos 1 y 2 del Proyecto Inicial**.  
El objetivo es construir un simulador inspirado en el problema **“The Silk Road … with Robots!”** de la Maratón de Programación ICPC 2024.  

El simulador implementa un escenario en el que **robots recorren una ruta para visitar tiendas y obtener ganancias**, considerando la distancia y el dinero disponible en cada tienda.  
A lo largo de los ciclos, el proyecto evoluciona desde un simulador básico hasta incluir entradas estilo maratón y selección automática de la tienda más rentable.

---

## 🎯 Requisitos Funcionales

### Ciclo 1
- Crear una ruta de seda dada su longitud.  
- Adicionar/eliminar tiendas y reabastecerlas.  
- Adicionar/eliminar robots y retornarlos a posiciones iniciales.  
- Mover un robot manualmente a una tienda.  
- Reiniciar la ruta de seda.  
- Consultar ganancias acumuladas e información de la ruta.  
- Mostrar/ocultar el simulador.  
- Terminar el simulador.  

### Ciclo 2
- **Mover un robot automáticamente** a la tienda más rentable (`moveRobotToBestStore`).  
- **Leer entradas estilo maratón** (`createFromMarathonInput`) para crear múltiples tiendas desde datos en formato competitivo.  
- **Mantener reglas de desempate**: en caso de igualdad en la rentabilidad, el robot debe elegir la tienda con menor id.  
- Probar condiciones especiales (sin robots, sin tiendas, entradas vacías, empates).  

---

## 🛠️ Requisitos de Construcción
- Uso de **BlueJ** en un proyecto llamado `silkroad`.  
- Respeto a las decisiones de diseño establecidas en la clase principal (`SilkRoadSimulator`).  
- Uso y extensión del paquete **`shapes`** para la representación visual (tiendas y robots con colores y figuras).  
- Implementación documentada en Java con **Javadoc**.  

---

## 📑 Entregables
- **Diseño en Astah:**  
  - Diagramas de clases (Ciclo 1 y 2).  
  - Diagramas de secuencia de los métodos principales.  
- **Código en Java:**  
  - Bien estructurado, con estándares de codificación y documentación.  
- **Pruebas de Unidad:**  
  - Clase `SilkRoadC2Test` (obligatoria).  
  - Clase `SilkRoadCC2Test` (colaborativa en Wiki, con iniciales de los autores).  
- **Retrospectiva del trabajo:**  
  - Documentación sobre mini-ciclos, logros, dificultades y compromisos de mejora.  
- **Pruebas de aceptación:**  
  - Casos preparados para la sustentación.  

---

## 🚀 Cómo usar el simulador
1. Crear una instancia de `SilkRoadSimulator` indicando la longitud de la ruta:  
   ```java
   SilkRoadSimulator sim = new SilkRoadSimulator(50);
   ```
2. Agregar tiendas y robots:  
   ```java
   sim.addStore(1, 5, 10, "red");
   sim.addRobot(1, 0, "yellow");
   ```
3. Mover robots de forma manual:  
   ```java
   sim.moveRobot(1, 1);
   ```
4. O moverlos automáticamente a la tienda más rentable:  
   ```java
   sim.moveRobotToBestStore(1);
   ```
5. Cargar entrada estilo maratón:  
   ```java
   List<String> lines = Arrays.asList("2 5 10 8 20", "1 15 30");
   sim.createFromMarathonInput(lines);
   ```
6. Consultar resultados:  
   ```java
   System.out.println(sim.getRouteInfo());
   System.out.println("Ganancia: " + sim.getProfit());
   ```

---

## 👥 Autores
- Camilo Aguirre  
- Mateo Sánchez  
