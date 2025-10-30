# Java basics

## Tipos de dato

1.  primitivos: int, double, boolean, char, etc.
2.  No primitivos (referenciados): clases, arrays y objetos.

## Clases y objetos

Una clase es una plantilla par crear un objeto.
un objeto es una instancia de esa plantilla.

## Metodos

bloques de codigo que ejecutan una tarea; pueden tener parametros y valores de retorno.

## Modificadores de acceso

1.  public: se puede acceder de donde sea 
2.  private: se puede acceder solo dentro de la clase
3.  protected: se puede acceder dentro del paquete y subclases
4.  default: pueden ser accedidos por otras clases dentro del mismo paquete (no por subclases)

## constructores

inicilizan objetos; pueden ser sobrecargados.


### Ejemplo basico de una clase

```java
public class Persona{
    private String nombre;
    private int edad;

    public Persona (String nombre, int edad){
        this.nombre = nombre;
        this.edad = edad;
    }

    public void saludar(){
        System.out.println("Hola, Soy " + this.nombre);
    }


}

```

# Poo

## Herencia

Permite que una clase (hija o subclase) herede atributos y metodos de otra clase (padre o superclase).

Caso de Uso: en un sistema empresarial, tienes jerarquias como empleado, gerente, desarrollador, interno. todos comparten comportamiento base (nombre, salario) pero pueden tener
metodos adicionales.

Buenas practicas:

1.  Evita herencias muy profundas ya que son dificiles de mantener.
2.  Usa herencia cuando la relacion sea "es un" ejemplo "un gerente "es un" empleado".
3.  Considera composicion sobre herencia si la relacion es "tiene un".

### Ejemplo

```java
class Empleado{
    protected String nombre;
    protected double salario;

    public Empleado(String nombre, double salario){
        this.nombre = nombre;
        this.salario = salario;
    }
}

class Gerente extends Empleado{
    private double bono;

    public Gerente(String nombre, double salaario, double bono){
        super(nombre, salario);
        this.bono = bono;
    }

    public void aprobarProyecto(){
        System.out.println(nombre+" aprobo un proyecto");
    }
}


```
## Polymorphismo

Permite que un mismo metodo se comporta de manera diferente segun el objeto que lo invoque

hay dos tipos de polomorfismo
1.  Polimorphismo en tiempo de compilacion (sobrecarga).
2.  Polimorphismo en tiempo de ejecucion (sobreescritura).

Caso de uso real:
Una lista de objetos "Animal" donde cada elemento puede ser "Perro", "Gato", "Ave", etc. pero todos pueden ser procesados por el mismo metodo generico "hacerSonido()".

Buenas practicas:

-   usa `@Override` para evitar errores al sobreescribir.
-   Diseña clases para depender de interfaces o clases base, no implementaciones concretas (principio de inversion de dependencias en SOLID).

### Ejemplo de Polymorphismo

```java
class Animal{
    public void hacerSonido(){
        System.out.pringln("Sonido generico");
    }
}

class Perro Extends Animal{
    @Override
    public void hacerSonido(){
        System.out.println("Guau!");
    }
}

class Gato extends Animal{
    @Override
    public void hacerSonido(){
        System.out.println("Miau!!");
    }
}

```

## Manejo de excepciones 

Permite manejar errores sin detener abruptamente el programa.

bloque clave:

-   try: contiene el codigo que puede causar una excepcion.
-   catch: Captura y maneja la excepcion.
-   finally: se ejecuta siempre (se usa para liberar recursos).
-   throw/throws: para lanzar o propagar excepciones.

Caso de uso real: el manejo de erores de conexion a bases de datos, lectura de archivos o llamadas HTTP que pueden fallar.

Buenas practicas:

-   Captura solo las excepciones que puedes manejar.
-   Usa excepciones personalizadas para controlar el flujo normal del programa.
-   Limpia recursos como streams o conexiocnes en "finallY" o usa "try-with-resources".

## Ejemplo

```java
public class Division {
    public static int dividir(int a, int b) {
        try {
            return a / b;
        } catch (ArithmeticException e) {
            System.out.println("Error: Division entre cero no esta permitido");
            return 0;
        } finally {
            System.out.println("Operacion Finalizada");

        }
    }
}

```

## interfaces

Una interfaz define un contrato (que metodos deben implementarse) sin definir como. permiten la abstraccion y el desacoplamiento entre componentes.

Caso real: un sistema de pagos, puesdes tener diferentes implemencaciones como "TargetaCredito", "Paypal", "Criptomoneda", todas usando la misma interfaz "Pagable".
esto permite cambiar el metodo de pago sin Modificar el resto del codigo.

Buenas practicas: 
-   Nombra las interfaces como capcidades o comportamientos ej. "Comparable", "Serializable" o "Runnable".
-   Usa interfaces para permitir inyeccion de dependencias y pruebas unitarias.
-   No abuses de interfaces si no hay necesidad real de desacoplar.

### Ejemplo de interfaces

```java

interface Pagable{
    void procesarPago(double cantidad);
}

class TargetaCredito implements Pagable{

    @Override
    public void procesarPago(double cantidad) {
        System.out.println("Pago procesado con targeta: $"+cantidad);
    }
}

class Paypal implements Pagable{

    @Override
    public void procesarPago(double cantidad) {
        System.out.println("Pago procesado con Paypal: $"+cantidad);
    }
}



```

## Conexion entre los conceptos

1.  Herencia: permite reutilziar codigo y comportamientos comunes.
2.  Polimorfismo: permite tratar objetos de forma generica.
3.  Intercaes: definen contratos comunes para distintas implementaciones.
4.  Excepciones Garantizan que los errores se manejen sin romper la ejecucion.
