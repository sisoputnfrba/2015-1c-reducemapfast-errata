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

