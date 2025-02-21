# Analisis realacionado a clase `Tablero`


## proyecto de Juego de damas

```java
    public class Tablero {
    private final Casilla[][] tablero = new Casilla[8][8];;

    public Tablero() {
        inicialCasilla1();
        inicialCasilla2();
        inicialCasilla3();
    }

    public void dibujarTablero() {
        
    }
    
    private void inicialCasilla1() {
        
    }
}
```

## **1. Code Smells de Diseño**

### **1.1 Duplicación de Código**
- **Descripción:** Los métodos `inicialCasilla1()`, `inicialCasilla2()` e `inicialCasilla3()` tienen una estructura muy similar y solo varían en los valores asignados a `Casilla`.
- **Solución:** Crear un solo método que reciba parámetros para definir el comportamiento de cada sección del tablero.

### **1.2 Clases con demasiadas responsabilidades**
- **Descripción:** La clase `Tablero` maneja la lógica de inicialización, dibujo, movimientos y validaciones, lo que la hace poco cohesiva.
- **Solución:** Extraer responsabilidades en clases separadas, como una `TableroInicializador` y `TableroRenderer`.

---

## **2. Code Smells de Código**

### **2.1 Código Muerto**
- **Descripción:** La variable `esColorIteracion` se inicializa en los métodos `inicialCasilla1()`, `inicialCasilla2()` e `inicialCasilla3()`, pero se sobrescribe en el primer ciclo del bucle.
- **Solución:** Eliminar la inicialización innecesaria.

### **2.2 Métodos con nombres poco descriptivos**
- **Descripción:** Métodos como `jugable()`, `derecha()`, `casillaOcupada()` tienen nombres poco claros.
- **Solución:** Renombrarlos con nombres más expresivos, como `esCasillaJugable()`, `esMovimientoALaDerecha()`, `estaCasillaOcupada()`.

---

## **3. Code Smells de Mantenimiento**

### **3.1 Números Mágicos**
- **Descripción:** El código contiene números como `3`, `5`, `8`, `2`, sin contexto de su significado.
- **Solución:** Reemplazar con constantes como `FILAS_TABLERO`, `COLUMNAS_TABLERO`, `SALTO_VALIDO`.

### **3.2 Falta de Encapsulamiento**
- **Descripción:** El array `tablero` se manipula directamente dentro de la clase, lo que puede llevar a inconsistencias.
- **Solución:** Crear métodos `getCasilla()` y `setCasilla()` para acceder/modificar la estructura de datos de manera controlada.

