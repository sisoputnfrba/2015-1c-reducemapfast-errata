ReduceMapFast - Fe de erratas
=============================

* Al pie de la página 13 del enunciado, la tabla indica que tanto `datos` como `fotos` son directorios cuyo padre es el directorio `2`, pero en la misma tabla está `jose` en lugar de `juan`. La tabla correcta sería:

| Index | Directorio | Padre |
|-------|------------|-------|
|   1   | user       |   0   |
|   2   | juan       |   1   |
|   3   | jose       |   1   |
|   4   | temporal   |   0   |
|   5   | datos      |   2   |
|   6   | fotos      |   2   |

* En la página 11, sección "Redundancia", el enunciado dice:
> Al recibir una operación de escritura deberá balancear la asignación de los bloques entre todos los Nodos del sistema junto con evitar que el mismo bloque de datos de un archivo más de una vez en el mismo nodo.

La frase debería decir:
> Al recibir una operación de escritura, deberá balancear la asignación de los bloques entre todos los Nodos del sistema, evitando que en un mismo Nodo exista más de una copia de algún bloque.

* En la página 15, el enunciado especifica eventos que el proceso FileSystem debe loggear en Pantalla. Dado que la terminal en que se ejecute este proceso quedará tomado por la Consola del FileSystem para interactuar con el usuario, no se deberá loggear ningún evento por pantalla, a fin de que los mensajes no interrumpan al usuario.

* En los Parámetros de Configuración del proceso FileSystem (páginas 14 y 15), el enunciado dice que tendrá una:
> Lista de nodos mínima que deben estar conectados para que el FileSystem pase a estado Operativo

En realidad, el proceso FileSystem no tendrá como configuración una lista de Nodos que necesita que estén levantados, si no una cantidad de Nodos que deben estar conectados para arrancar.

* Para pasar al estado Operativo, el FileSystem deberá esperar a que se le conecten una cantidad mínima de Nodos, especificada por archivo de configuración. A partir de ese momento, el FileSystem se mantendrá Operativo durante toda la vida del proceso.

Los archivos se mantendrán Disponibles mientras esté accessible al menos una copia de cada uno de sus bloques de datos.

Una operación de agregado de un archivo al FileSystem será exitosa sólo si se pueden crear al menos 3 copias (en Nodos distintos) de cada uno de sus bloques de datos. Si esto no fuera posible, la operación deberá fallar sin ocupar bloques de datos.

* El proceso Nodo deberá ejecutar todas sus tareas de Map y Reduce de manera concurrente
