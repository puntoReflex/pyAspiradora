# Análisis del algoritmo

## Análisis de componentes clave

### Inicialización (contaminate)

```java
for (int row = 0; row < aMap.length; row++) {
    for (int column = 0; column < aMap[row].length; column++) {
        aMap[row][column] = (int) (Math.random() * 5);
    }
}
```

Complejidad: O(n*m) donde n,m son las dimensiones del mapa

### Movimiento (moveVacuum)

```java
int[] movement = directions[(int) (Math.random() * directions.length)];
vacuumPosition[0] = vacuumPosition[0] + movement[0];
vacuumPosition[1] = vacuumPosition[1] + movement[1];
```

Complejidad: O(1) por iteración

### Verificación de Limpieza (isDirty)

```java
for (int row = 0; row < surface.length; row++) {
    for (int column = 0; column < surface[row].length; column++) {
        if (surface[row][column] > 0) return true;
    }
}
return false;
```

Complejidad: O(n*m)

## Análisis de complejidad

### Por iteración

- Movimiento: O(1)
- Limpieza: O(1)
- Verificación: O(n*m)
- Visualización: O(n*m)

Total por iteración: O(n*m)

### Número de iteraciones

- Cada celda puede necesitar hasta 4 visitas
- El movimiento aleatorio no garantiza cobertura eficiente
- Teóricamente: O(k·n·m) iteraciones donde k depende de:
  - Nivel máximo de suciedad (4)
  - Ineficiencia del movimiento aleatorio

### Complejidad total

- Teórica: O((n*m)²)
- Práctica: Limitada por dimensiones fijas (10x25)

## Consideraciones especiales

### Movimiento aleatorio

- No garantiza cobertura uniforme
- Puede revisitar celdas innecesariamente
- Podría nunca alcanzar algunas celdas (aunque improbable)

### Niveles de suciedad

- Máximo 4 visitas por celda
- Limpieza gradual (no instantánea)
- Estado global mejora monotónicamente

## ¿Y ahora qué?

Este análisis sugiere varias áreas de mejora y estudio:

<div align=center>

|Optimizaciones|Variantes del problema|Aplicaciones similares|Mejoras de análisis|
|-|-|-|-|
|Movimiento sistemático en lugar de aleatorio|Múltiples aspiradoras|Algoritmos de cobertura|Métricas de eficiencia|
|Priorización de celdas más sucias|Obstáculos en el mapa|Robots de pintura|Estadísticas de cobertura|
|Tracking de celdas visitadas|Suciedad que se regenera|Sistemas de vigilancia|Patrones de movimiento óptimos|
|Pathfinding inteligente|Diferentes patrones de movimiento|Exploración de terreno|Balance entre exploración y limpieza|

</div>
