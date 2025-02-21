# Analisis realacionado a clase `Manejador`

## proyecto de Juego de damas


```java
    public class Manejador {

        private Jugador[] jugadores = new Jugador[10];
        private Jugador jugCompetidor[] = new Jugador[2];

    public void ingresoJugador(){
        ....
    }
    
    public void jugadoresLista(){
        ....
    }
}
```
### `Hallazgos`
1. **Large Class (Clase Grande)**
- **Problema**:
La clase `Manejador` tiene demasiadas responsabilidades: maneja jugadores, realiza la selección de competidores, gestiona la lógica del juego y el almacenamiento de datos.

**Solución:**
Dividir la clase en múltiples clases:
- `GestorJugadores` (manejo de jugadores)
- `JuegoPPT` (gestión del juego de Piedra, Papel o Tijeras)
- `SeleccionadorCompetidores` (selección de jugadores para competir)

2. **Feature Envy (Envidia de Características)**
- **Problema**:
Los métodos `jugarPPTijera()` y `ganadorPPTij()` acceden frecuentemente a los métodos de `Jugador`, lo que indica que probablemente estos métodos deberían estar dentro de `Jugador` o `MiniJuego`.

**Solución**:
Mover la lógica de `jugarPPTijera()` y `ganadorPPTij()` a la clase `MiniJuego` o `Jugador`.

3. **Long Method (Métodos Largos)**
**Problema**:
Métodos como `ingresoJugador()`, `jugarPPTijera()` y `ordenamiento()` tienen demasiadas líneas de código, lo que dificulta su comprensión y mantenimiento.

**Solución**:
Dividir estos métodos en submétodos más pequeños y específicos.

4. **Duplicated Code (Código Duplicado)**
**Problema:**
Los bucles `for` en `iniciar()` para asignar `partidasGanadas` y `partidasPerdidas` son idénticos.

**Solución:**
Fusionar estos bucles en uno solo y usar un método auxiliar para asignar ambos valores.

5. **Magic Numbers (Números Mágicos)**
** Problema:**
El uso de valores constantes como `new Jugador[10]`, `Math.random()*5`, y verificaciones como `if (aux == 1)` hacen que el código sea difícil de entender y modificar.

### Solución:
Definir constantes con nombres descriptivos, por ejemplo:
```java
private static final int MAX_JUGADORES = 10;
private static final int MAX_PARTIDAS = 5;
```

6. **Switch Statements (Uso Excesivo de Switch/If)**
**Problema:**
La selección de fichas en `elgirFicha()` está implementada con `if` en lugar de usar un `enum` para representar los tipos de fichas.

**Solución:**
Definir un `enum Ficha { AMARILLO, NEGRO }` y usarlo en lugar de valores enteros.

7. **Shotgun Surgery (Cirugía de Escopeta)**
**Problema:**
Si hay que cambiar la forma en que se seleccionan los jugadores, hay que modificar varios métodos dispersos.

**Solución:**
Extraer la selección de jugadores a una clase separada `SeleccionadorCompetidores`.

## Conclusión
El código de `Manejador` sufre de varios Code Smells relacionados con clases y diseño. La clase tiene muchas responsabilidades, nombres pocos descriptivos, muchas anidaciones en los algoritmos

