# Basic UNIX and LINUX Commands

## File Handling (manejo de archivos y directorios)

-   pwd: muestra el directorio actual para saber en cual estas.
-   ls: lista archivos / muestra el contenido de un directorio.
-   cd: Cambia de directorio por ejemplo `cd /home/user`.
-   mkdir: Crea un directorio por ejemplo `mkdir logs`.
-   rmdir / rm -r: elimina directorios `rm -r logs`.
-   cp: copia archivos `cp archivo1.txt copia.txt`.
-   mv: Mueve o renombra `mv viejo.txt nuevo.txt`.
-   cat: muestra el contenido de un archivo `cat archivo.txt`.
-   head/tails: Muestra primeras o ultimas lineas `tail -n 10 archivo.log` 
-   touch: crea un archivo vacio `touch notas.txt`.
-   rm: Borrar archivos `rm archivos.txt`.

### Buenas practicas de File Handling

-   usa `ls -lh`para ver tamaño legible.
-   Cuidado con `rm -rf /` puede borrar todo el sistema.
-   Usa `tab` para autocompletar rutas.

## grep

`grep` busca lineas que coinciden con un patron dentro de archivos o salidas de comandos. es una herramienta poderosa para logs o scripts

sintaxis

```bash
grep [opciones] "patrón" archivo.

grep "ERROR" app.log 
```


| Comando                   | Descripción                      |
| ------------------------- | -------------------------------- |
| `grep "palabra" archivo`  | Busca coincidencias simples      |
| `grep -i "error" archivo` | Ignora mayúsculas/minúsculas     |
| `grep -r "texto" /ruta`   | Busca recursivamente en carpetas |
| `grep -n "error" archivo` | Muestra número de línea          |
| `grep -v "INFO" archivo`  | Excluye líneas con “INFO”        |
| `grep java`               | Filtra procesos con “java”       |

## find

Busca archivos en el sistema con filtros por nombre, tamaño, tipo o fecha.

`find [ruta] [criterios] [acciones]`

ejemplo

```bash
find /home -name "*.txt"
```
Encuentra todos los archivos .txt dentro de /home.

ejemplos utiles

| Comando                            | Descripción                                   |
| ---------------------------------- | --------------------------------------------- |
| `find . -type f -name "*.log"`     | Busca archivos `.log` en el directorio actual |
| `find /var -type d -name "backup"` | Busca directorios llamados “backup”           |
| `find . -size +10M`                | Archivos mayores a 10 MB                      |
| `find . -mtime -7`                 | Archivos modificados en los últimos 7 días    |
| `find . -name "*.tmp" -delete`     | Borra archivos temporales                     |

### Buenas practicas

find tambien se puede combinar con -exec para ejecutar acciones 

```bash
find . -name "*.bak" -exec rm {} \;
```

Usa -print para verificar antes de eliminar.

## chmod para permisos de archivos

chmod cambia los permites de lectura (`r`), escritura (`w`) y ejecucion (`x`).

Estructura de permisos:

```makefile
r = 4, w = 2, x = 1

Ejemplo:  rwxr-xr--
          7  5  4

```
sintaxis

`chmod [opciones] permisos archivo`

```bash
chmod 755 script.sh
```

# Shell scripting basics

Un shell script es un archivo de texto que contiene una serie de comandos Unix/Linux que se ejecutan secuencialmente.

Estructura basica: 

```bash
#!/bin/bash

echo "Inicio del script"

# Variables

NOMBRE="Daniel"

# Condicional
if [ -f "/etc/passwd"]; then
    echo "Archivo existe"
fi

for i in {1..3}
do
    echo "Iteracion $i"
done

```

Ejemplo de un script real

```bash
#!/bin/bash
# backup.sh

FECHA=$(date +%Y-%-%d)
DESTINO="/bashups/backup_$FECHA.tar.gz"

tar -czf $DESTINO /home/usuario/proyecto

echo "Backup creado en: $DESTINO"
```
Ejecucion

```bash
chmod +x backup.sh
./backup.sh
```

este script respalda un archvo, automatizas despliegues o tareas repetitivas.


## elementos de scripting

| Elemento          | Ejemplo                         | Descripción                      |
| ----------------- | ------------------------------- | -------------------------------- |
| Variables         | `nombre="Ana"`                  | Almacenar valores                |
| Parámetros        | `$1`, `$2`, `$@`                | Argumentos al ejecutar el script |
| Condicional       | `if [ $x -gt 10 ]; then ... fi` | Lógica condicional               |
| Bucles            | `for`, `while`, `until`         | Repetir acciones                 |
| Comandos en línea | `fecha=$(date)`                 | Captura salida de un comando     |
| Comentarios       | `# Esto es un comentario`       | Documentar código                |
