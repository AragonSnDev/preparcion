# SCRUM Basics

## Que es agile?

Es una metodologia de trabajo enfocada en la entrega continua de valor, la colaboracion y la adaptavilidad al cambio.

Se basa en el manifesto agil que prioriza:

1.  Individous en interacciones sobre procesos y herramientas.
2.  Software funcionando sobre documentacion extensa.
3.  Colaboracion con el cliente sobre negociacion de contratos.
4.  Respeusta al cambio sobre seguir un plan rigido.

El objetivo es entregar software de calidad en interacciones cortas y ajustarse rapidamente a nuevas necesidades.


## Basicos de scrum

Scrum es un marco de trabajo agil que organiza el desarrollo en roles, eventos y artefactos

### Roles Principales

1.  Product Owner (PO): Se encarga de priorizar el backlog, define que se construye y asegura que el producto entregue valor.
2.  Scrum Master (SM): Facilita el proceso Scrum, elimina bloqueos y mejora la dinamica del equipo.
3.  Development team: Desarrollan , prueban y entregan incrementeos de software funcional.

## Artefactos de scrum

-   Product backlog: Lista priorizada de todas las funcionalidades, bugs y mejoras (historias de usuario).
-   Sprint backlog: Subconjunto del backlog que el equipo se compromete a completar en el sprint actual.
-   Increment: producto funcional entregado al final de cada sprint, es el valor tangible que se agrega al proyecto.

### Buenas practicas

-   Mantener el backlog siempre actualizado.
-   Definir claramente el "Definition of Done" Criterio de completitud.
-   Fomentar la comunicacion abierta en el equipo.
-   Adaptar el proceso segun lo que funcione mejor en cada sprint.

# Sprints

Es un ciclo de trabajo corto (normalementre entre 1 a 4 semanas) en el que sel equipo desarrolla y entrega un incremento funcional del producto.

el objetivo de cada sprint es producir algo entregable y funcional, aunque no sea el producto final completo.

## Fases dentro de un Sprint

1.  Sprint Planning
    -   El equipo selecciona del backlog los items que puede completar.
    -   Se define el Sprint Goal (objetivo del sprint) como implementar un modulo de login con validacion JWT.
2.  Daily Stant-up (reuniones diarias)
    -   cada miembro responde 3 preguntas.
        -   ¿Que hice ayer?
        -   ¿Que hare hoy?
        -   Tengo algun bloqueo?
    ejemplo: "ayer termine el endpoint de login; hoy empiezo pruebas; no tengo bloqueos".
3.  Sprint Review:
    -   El equipo reflecxiona sobre que funciono, que no y como mejorar.
    -   Las pruebas unitarias tromaron mas tiempo, deberiamos automatizarlas.

## Buenas practicas para los sprints

-   Mantener la duracion constante (ej. siempre 2 semanas).
-   No agregar tareas nuevas durante el sprint sin consenso.
-   Enfocarse en cumplir el objetivo del sprint, no en "llenarlo de trabajo".
-   Revisar la velocidad del equipo (velocity) para planear futuros sprints.

# Stand-ups (o daily scrums)

Reunion rapida diario (maximo 15 minutos) donde el equipo sincroniza su progreso.

Objetivo: detectar bloqueo, coordinar esfuerzos y mantener la transparencia.

## Buenas practicas

-   Reuniones de pie (literalmente) para mantenerla breve.
-   No convertira en unsa sesion de reporte al jefe.
-   Evitar discutir detalles tecnicos largos; anotar y resovler despues.
-   Maneter un horario fijo.

# Backlog grooming

Tambien llamado como refinemente meeting, es una reunion (una vez por sprint) donde el equipo y product ownes revisan y priorizan y detallan las hisotiras de prodcut backlog.

el objetivo es asegurar que las tareas esten claras, estimadas y listas para ser trabajadas en el siguiente sprint.

## Actividades comunes

-   Revisar y re-priorizar historias segun el valor de negocio.
-   Dividir tareas grander (epicar) en historais mas pequeñas.
-   Estimar esfuerzo usando story points o planning poker.
-   Detectar dependencias o riesgos antes del siguiente spring.

Ejemplo

El backlog contiene "implementar un modulo de reportes".

Durante el grooming se divide en:
1.  Crear endpoing `/reports/sales`.
2.  Crear componente frontend de reportes.
3.  Agregar exportacion a PDF.

## Buenas practicas

-   Hacer grooming regularmente (1-2 veces por sprint).
-   Involucrar siemrpe al product owner.
-   Mantener las historias clarar, pequeñas y con criterior de aceptacion definidos.
-   usar herramientas como jira, trello o azure boards.

