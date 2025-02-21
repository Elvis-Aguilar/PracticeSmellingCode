# Analisis realacionado a clase `Manejador`

## proyecto de Juego de damas


```java
public class LectorArchivoTxt {

    private String inicioTablero = "tablero(";
    private String pierdeTurno = "pierdeturno(";
    private String tirarDado = "tiradados(";
    private String avanz = "avanza(";
    private String retroceso = "retrocede(";
    private String subida = "subida(";
    private String bajada = "bajada(";
    private  int[] dimenciones = new int[2];
    public  int[] pierdeTur = new int[30];
    public  int[] tiradado = new int[30];
    public  int[] avanza = new int[60];
    public  int[] retroces = new int[60];
    public  int[] subid = new int[100];
    public  int[] bajad = new int[100];

    public LectorArchivoTxt(){
        inicializar();

    }

    public void leerFichero(File archivo,JTextArea text) throws FileNotFoundException, IOException {
        

    }
}
```

## 1. **Code Smells de Más Lógica de la Necesaria** (Bloaters)
### 1.2 **Long Method**
El método `separarCampos(String linea)` es excesivamente largo y complejo. Tiene demasiadas verificaciones `if` anidadas, lo que hace que su comprensión y mantenimiento sean difíciles.

### 1.2 **Large Class**
La clase `LectorArchivoTxt` maneja demasiadas responsabilidades:
- Leer un archivo.
- Parsear su contenido.
- Almacenar información en arreglos.
  Esto viola el principio de responsabilidad única (SRP).

## 2. **Code Smells de Acoplamiento Excesivo** (Couplers)
### 2.1 **Feature Envy**
El método `separarCampos()` accede directamente a las variables de la clase para modificar los arreglos. Sería mejor que estas modificaciones se encapsulen dentro de la clase correspondiente.

### 2.2 **Inappropriate Intimacy**
El código tiene una relación demasiado cercana con `JTextArea`, lo que lo hace dependiente de la interfaz gráfica. La clase debería centrarse solo en la lógica de procesamiento de archivos.

## 3. **Code Smells de Dispersión y Redundancia** (Dispensables)
### 3.1 **Duplicate Code**
La manipulación de `lineaDeCampos`, `campos` y la verificación con `verificacion(campos)` se repite en varias partes del código.

### 3.2 **Magic Numbers**
Los arreglos tienen tamaños fijos (`30`, `60`, `100`), lo cual hace que el código sea menos flexible.

## 4. **Code Smells de Mala Comprensión** (Change Preventers)
### 4.1 **Shotgun Surgery**
Si el formato del archivo cambia, hay que modificar muchos `if` dentro de `separarCampos()`, lo que hace que sea propenso a errores.

### 4.2 **Divergent Change**
Si en el futuro se quiere soportar más tipos de comandos en el archivo, habrá que seguir agregando más `if` a `separarCampos()`, haciendo que el código sea más difícil de mantener.
