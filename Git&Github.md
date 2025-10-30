#   Git

Git es un sistema de control de versiones distribuido. permite registrar los cambios en el codigo a lo largo del tiempo y volver a versiones anteriores.

#   Git hub

Github es una plataforma en la nume para alojar repositorios GIT, colaborar con otros desarrolladores, hacer revisiones de codigo y manejar verisones de proyectos.


#   Cloning

Clonar significa descargar una copia completa de un repositorio remoto (por ejemplo de github) en tu mmaquina local.

comando:

```bash
#git clone <url-del-reposiotorio >
git clone https://github.com/danielaragon/proyecto-java.git
```

Este comando crea una carpeta local con todo el codigo, ramas y commits del proyecto.

## Buenas practicas

-   usa SSH si trabajas frecuentemente.
-   Verifica con `git remote -v` para confirmar la conexion al repositorio remoto.

#   Commits


un commit es un punto de guardado del codigo: registra que cambio quien lo hizo y cuando lo hizo.

comandos tipicos 

se usa junto con `git add archivo.java` para preparar el archivo para se commiteado.

```bash
git add archivo.java        # Preparar archivo para commit
git commit -m "Mensaje claro del cambio"
```

Buenas practicas de commit

-   Mensajes descriptivos (en presente o imperativo)
-   Commits pequeños y frecuentes (por funcionalidad).
-   Reviza antes de hacer commit con `git statu`s y `git diff`

#   Push/Pull/Fetch

Push envia commits locales al repositorio remoto (GitHub).

```bash
git push origin main
git push origin feature/login

```

Pull descarga y fusiona los ultimos cambios del remoto a tu rama local

```bash
git pull origin main
```

Buenas practicas

-   Siemrpe haz git pull antes de empezar a trabajar para evitar conflicots
-   No hagas push directo a main si el flujo de trabajo usa "Pull Requests"
-   Usa ramas como feature/bugfix/hotfix para cambios organizados.

#   Conflict Resolution

Un conflicto ocurre cuando dos personas editan la misma linea o seccion de un archivo y git no sabe cual conservar

ejemplo real:

-   Tú cambias una función en main.java.
-   Otro compañero también la cambia y hace push.
-   Cuando haces git pull, Git detecta conflicto.

un conflicto se ve de la siguiente manera

```java
<<<<<<< HEAD
System.out.println("Versión mía");
=======
System.out.println("Versión del remoto");
>>>>>>> origin/main
```

## Como resolver conflictos

1.  abre el archivo del conflicto
2.  Edita manualmente para dejar la version correcta.
3.  guarda los cambios.
4.  marcalo como resuelto

```bash 
git add main.java
git commit -m "Resuelvo conflicto en main.java"
```

## Buenas practicas para evitar conflictos

-   Trabaja en ramas individuales (como `feature/nueva-funcionalidad`).
-   Sincroniza frecuentemente (`git pull origin main`).
-   haz pull despues de cada push.
-   Divide grandes cambios en commits pequeños.
-   usa git rebase con cuidado (util para limpiar historial pero puede reescribir commits).

# Comandos utiles de GIT

| Comando                     | Descripción                                    |
| --------------------------- | ---------------------------------------------- |
| `git status`                | Muestra archivos modificados y rama actual     |
| `git log --oneline --graph` | Historial visual de commits                    |
| `git branch`                | Lista ramas locales                            |
| `git checkout <rama>`       | Cambia de rama                                 |
| `git merge <rama>`          | Fusiona otra rama a la actual                  |
| `git diff`                  | Muestra diferencias entre versiones            |
| `git reset --hard <commit>` | Revierte a un commit anterior (⚠️ con cuidado) |


# Buenas practicas de GIT Globales

-   Commit temprano y frecuentemente.
-   usa ramas por feature o bug.
-   Mensajes de commit descriptivos.
-   Pull request conrevision antes de mergear.
-   .gitignore para excluir archivos innecesarios.
-   No subas contraseñas a apis.