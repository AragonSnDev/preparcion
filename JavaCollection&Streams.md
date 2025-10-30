# Collection & Streams

## Collections

Es un conjunto de interfaces y clases que permiten almacenar, ordenar y manipular datos en memoria de forma eficiente.

Estas incluyen

-   List.
-   Set.
-   Map.

### List

Colleccion ordenada, que permite elementos duplicados y se accede por indice.

Casos de uso: 
-   Listas ordenadas de datos como (usuarios, productos y registros).
-   Cuando importa el orden de insercion o se requirer acceso por indice.

Buenas practicas de List

-   ArrayList para acceso rapido y pocas insercines intermedias.
-   LinkedList cuando hacer muchas inserciones/eliminaciones en medio de la lista.

#### Ejemplo de List

```java 
List<String> nombres = new ArrayList<>();
nombres.add("Ana"); 
nombres.add("Luis"); 
nombres.add("Ana"); // Duplicado permitido. 
```

### Set

Coleccion sin elementos duplicados, el orden depende de su tipo de implementacion (si es HashSet, LinkedHashSet, TreeSet).

Casos de uso:

-   Evitar duplicados (IDs unicos, correos, nombres de usuario).
-   Verificar pertenencia con el metodo `contains()` ya que es muy eficiente en HashSet.

Buenas Practicas

-   HashSet si no importa el orden.
-   TreeSet si necesitas elementos ordenados naturalmente (alfabeticamente o numericamente).

#### Ejemplo de Set

```java
Set<String> frutas = new HashSet<>();
frutas.add("Manzana");
frutas.add("Pera");
frutas.add("Manzana"); //No se agrega
```

### Map

Estructura que almacena pares clave-valor, cada clavem es unica pero los valores pueden repetirse

Casos de uso:
-   Almacenar relaciones tipo diccionario o ID-valor.

Buenas Practicas:
-   Usa HashMap para busquedas rapidas.
-   LinkedHashMap si necesitas mantener el orden de insercion.
-   TreeMap para claves ordenadas

#### Ejemplo de Map

```js
Map<Integer,String> empleados = new HashMap<>();
empleados.put(1,"Daniel");
empleados.put(2,"Maria");
empleados.put(3,"Daniel"); // Valor duplicado permitido pero con clave unica.
```


### Iteracion sobre coleccion

```java
List<String> lista = List.of("A","B","C");

// for tradicional
for(int i = 0; i<lista.size();i++){
    System.out.println(Lista.get(i));
}

// for-each
for(String elemento : lista){
    System.out.println(elemento);
}

//forEach con lambda
lista.forEeach(e->System.out.println(e));

```

Buenas practicas de iteracion de collecciones

-   Usa forEach o Streams para codigo mas limpio.
-   Evita modificar una coleccion mientras la recorres (usa Iterator.remove() si es necesario).

## Stream API

Libreria que permite procesar colecciones de forma declaratica y funcional (map, filter, reduce).
No modifica la coleccion original sino que genera nuevos resultados.

Ventajas: 
-   Codigo mas limpio y conciso.
-   Posibilidad de procesamiento paralelo con `.parallelStream()`.
-   Ideal para filtrado, mapeo y agregaciones.

Ejemplo basico de Stream

```java

// Filtrar nombres que comiencen con L, transformalos a UpperCase, ordenarlos y regresarlos
List<String> nombres2 = List.of("Ana","Luis","Carlos","Luisa");

List<String> filtrados = nombres2.stream()
        .filter(n -> n.startsWith("L"))
        .map(String::toUpperCase)
        .sorted()
        .collect(Collectors.toList());

System.out.println(filtrados);

// Reducir una lista de numeros a la suma de los numeros pares eliminado lo demas

```

### metodos

1.  .`filter()`: filtra elementos.
2.  `.map()`: transforma elementos.
3.  `.sorted()`: ordena elementos.
4.  `.limit(n)`: Toma los primeros n elementos.
5.  `.distint()`: elimina duplicados.
6.  `.collect()`: convierte el stream en una coleccion. 
7.  `.count()`: cuenta elementos.
8.  `.forEach()`: itera sobre el resultado.
9.  `.reduce()`: combina los elementos en un solo valor

### Buenas practicas de streams

1.  usar interfaces y no la clase de la interfaz al declarar las colecciones, facilita cambiar la implementacion sin modificar el resto del codigo.
2.  Evita colecciones isn tipo generico (raw types).
3.  Usa Streams cuando el procesamiento sea complejo o funcional.
4.  No abuses de los streams anidados oe excesivamente largos.
5.  Para rendimiendo, usa parallelStream() solo si el procesamiento es pesado.

