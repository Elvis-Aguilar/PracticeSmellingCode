# Analisis realacionado a clase `Juego`

## proyecto de Juego de damas

```java
public class Juego {
    public void iniciarJuego() {
        
    }

    public void movFicha() {
        
    }
}
```

## 1. **Code Smells de Diseño**

### 1.1. **Divergent Change**
- La clase `Juego` tiene demasiadas responsabilidades, como gestionar el flujo del juego, interactuar con los jugadores y manejar la lógica del tablero. Si en el futuro hay que hacer cambios en la lógica del juego, puede afectar múltiples partes de la clase.

### 1.2. **Shotgun Surgery**
- Si se cambia la forma en que los jugadores gestionan su turno, hay que modificar varias partes de la clase `Juego`, lo que indica un acoplamiento alto.

## 2. **Code Smells de Código Repetitivo**

### 2.1. **Duplicate Code**
- En el método `pedirPos()`, la lógica para obtener las coordenadas de los jugadores se repite dos veces, una para cada jugador. Esto se podría refactorizar en un método separado.

### 2.2. **Long Method**
- `iniciarJuego()` es un método demasiado largo y hace muchas cosas a la vez, lo que dificulta su comprensión y mantenimiento.

## 3. **Code Smells de Complejidad**

### 3.1. **Long Parameter List**
- El método `moverFicha()` usa muchas variables de instancia (`inicioI`, `inicioJ`, `finI`, `finJ`), lo que hace que el código sea menos claro. Tal vez podrían agruparse en una clase o estructura.

### 3.2. **Complex Conditional**
- En `perdedor()` y `pedirPos()`, se repiten estructuras de control anidadas que podrían simplificarse usando métodos auxiliares o expresiones más claras.

## 4. **Code Smells de Mala Nomenclatura**

### 4.1. **Inconsistent Naming**
- `jugPartida` no es un nombre claro para `Manejador`. Algo como `manejadorJugadores` sería más descriptivo.
- `movFicha()` debería llamarse `moverFicha()` para mantener consistencia con el resto del código.

### 4.2. **Misleading Name**
- `perdedor()` devuelve un `boolean` que indica si el juego debe continuar. Un nombre como `juegoContinua()` reflejaría mejor su propósito.

## 5. **Code Smells de Acoplamiento y Cohesión**

### 5.1. **Feature Envy**
- `Juego` accede demasiado a `jugPartida` para obtener información sobre los jugadores. Esto sugiere que parte de esta lógica debería estar dentro de `Manejador`.

### 5.2. **Message Chain**
- `jugPartida.getJugCompetidor()[0].getPiezsPerdidas()` es un claro ejemplo de un encadenamiento de mensajes que debería simplificarse con métodos más específicos en `Manejador` o `Jugador`.


