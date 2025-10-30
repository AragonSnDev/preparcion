#   SELECT

#   JOIN

Un JOIN se usa para combinar datos de dos o mas tablas basandose en una columna relacionada (con clave foranea).

## Tipos de JOIN

-   INNER JOIN: devuelve solo las filas que tienen coincidencias en ambas.
-   LEFT JOIN: Devuelve todas las filas de la tabla izquierda, aunque no haya coincidencia en la derecha. Las faltantes se llenan con NULL.
-   RIGHT JOIN: Devuelve todas las filas de la tabla derecha, aunque no haya coincidencias en la izquierda.
-   FULL JOIN: Devuelve todas las filas de ambas tablas, combinando las coincidencias y llenando con NULL donden falten datos.
-   CROSS JOIN: Combina cada fila de la primera tabla con cada fila de la segunda (producto cartesiano).

## Casos de uso

-   INNER JOIN: Ver empleados con su departamente, pedidos con su cliente, etc.
-   LEFT JOIN: Listar todos los empleados, incluso los que aun no tienen departamente asignado.
-   RIGHT JOIN: Ver todos los departamenteos, incluso los que aun no tienen empleados.
-   FULL JOIN: Auditorias o reportes donde se quieren ver datos no emparejados de ambos lados.
-   CROSS JOIN: Generar combinaciones de prueba o comparativas.

```sql
SELECT e.nombre, d.nombre AS departamento
FROM empleados e
INNER JOIN departamentos d
    ON e.departamento_id = d.id;

SELECT e.nombre, d.nombre AS departamento
FROM empleados e
LEFT JOIN departamentos d
    ON e.departamento_id = d.id;

SELECT e.nombre, d.nombre AS departamento
FROM empleados e
RIGHT JOIN departamentos d
    ON e.departamento_id = d.id;

SELECT e.nombre, d.nombre AS departamento
FROM empleados e
FULL JOIN departamentos d
    ON e.departamento_id = d.id;

SELECT e.nombre, d.nombre
FROM empleados e
CROSS JOIN departamentos d;
```

#   GROUP BY

GROUP BY Agrupa filas que tienen valores iguales en ciertas columnas para aplicar funciones de agrecacion como:

-   COUNT().
-   SUM().
-   AVG().
-   MIN().
-   MAX ().

#   Subconsultas

Una subconsulta es una consulta dentro de otra consulta, se puede usar en conjunto SELECT, WHERE, FROM, HAVING.

por ejemplo

```SQL
SELECT nombre, salario
FROM empleados
WHERE salario > (
    SELECT AVG(salario) FROM empleados
);
```

Muestra los empleados que tengan un salario mayor al promedio general.

```SQL
SELECT d.nombre, t.promedio
FROM (
    SELECT departamento_id, AVG(salario) AS promedio
    FROM empleados
    GROUP BY departamento_id
) t
JOIN departamentos d
    ON t.departamento_id = d.id;
```

Combinar agregaciones con otras tablas 

## Subconsultas con IN

```SQL
SELECT nombre
FROM empleados
WHERE id IN (
    SELECT empleado_id FROM proyectos WHERE activo = true
);
```

## Buenas practicas de subconsuultas

-   Usa subconsultas cuando no peudas resolverlo con un JOIN limpio
-   Prefiere siempre los JOINS para mayor rendimiento ya que las subconsultas son mas lentas.
-   Dale un alias a las subconsultas.

# UPDATE

Permite modificar valores existentes en una o mas filas.

```SQL
UPDATE empleados
SET salario = salario * 1.10
WHERE departamento_id = 3;

-- con JOINs

UPDATE empleados e
SET e.salario = e.salario * 1.05
FROM departamentos d
WHERE e.departamento_id = d.id
  AND d.nombre = 'Ventas';
```

## Buenas practicas de UPDATE

-   Siempre usar where para evitar modificar una tabla por error.
-   Haz un Select Prevvio con la misma condicion para verificar que filas afectara.
-   Usar transacciones cuando actualices un lote.