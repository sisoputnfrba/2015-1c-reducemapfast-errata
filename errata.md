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

* El MDFS deberá soportar la existencia de más de 3 copias de cada bloque de datos, y deberá tenerlas a todas en cuenta al momento de operar con ellos.

Por ejemplo, si se usara la operación Copiar bloque para generar una cuarta copia de un bloque en particular, el FS debería incluir esa cuarta copia como una posible ubicación de ese bloque cuando MaRTA le pida los bloques que componen un archivo.

* El FileSystem debe soportar cualquier cantidad de copias de cada bloque de datos de un archivo, pero aceptamos que el FS envíe a MaRTA únicamente 3 copias de cada bloque para planificar. Queda a discreción de cada grupo decidir cuáles de todas las copias disponibles elegir para enviar a MaRTA.

* En la página 22, el enunciado especifica que ante la salida de un Nodo del sistema durante o luego de rutinas map o reduce, se deberá re-planificar. Dada la complejidad de ciertos sistemas a adaptarse al requerimiento de re-planificar ante la falla de un reduce, se permite que en vez de re-planificar, el Job falle.

* ~~Los tamaños de los archivos que el sistema debe poder manejar superan los 2GB, por lo que se deben tomar en cuenta los siguientes recaudos:~~
> ~~Al utilizar la función `open()` ante archivos >2GB se debe compilar utilizando el flag `-D_FILE_OFFSET_BITS=64`. Ante la función `mmap()` se debe contemplar que no necesariamente se posea memoria suficiente en la memoria y en el Swap. Por lo tanto, se debe invocar a la función utilizando el flag `MAP_NORESERVE`.~~

* Los Nodos no necesitarán soportar Espacios de Datos mayores a 2GB, a fin de evitar inconvenientes con los archivos grandes en `mmap`.
