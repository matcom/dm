# Discreta II

## Clase Practica #3

1. Construya autómatas finitos no deterministas para reconocer los siguientes lenguajes. Trate de aprovechar al máximo la no determinación.

   1. El conjunto de cadenas sobre el alfabeto $\{0,1,...,9\}$ tal que el último dígito ha aparecido antes.

   2. El conjunto de cadenas sobre el alfabeto $\{0,1,...,9\}$ tal que el último dígito no ha aparecido antes.

   3. El conjunto de cadenas de 0's y 1's tal que hay dos 0's separados por una cantidad de posiciones que es un múltiplo de 4. Tenga en cuenta que 0 es un múltiplo permitido de 4.
2. Demuestre que las siguientes operaciones sobre lenguajes regulares son cerradas(esto es, que el resultado es un lenguaje regular). Las demostraciones deben ser formales, es decir, deben incluir la especificación del autómata que reconoce el lenguaje resultante o utilizar resultados de este propio ejercicio.

   1. Unión
   2. Concatenación
   3. Estrella de Kleene ( operación unaria que se aplica sobre un conjunto de cadenas de caracteres o un conjunto de símbolos o caracteres (alfabeto), y representa el conjunto de las cadenas que se pueden formar tomando cualquier número de cadenas del conjunto inicial, posiblemente con repeticiones, y concatenándolas entre sí.)¹
   4. Intersección
   5. Diferencia
   6. Complemento
   7. Reverso
   8. zip (operación binaria que se aplica sobre dos conjuntos de cadenas de caracteres y representa el conjunto de las cadenas que se pueden formar tomando una cadena de cada conjunto inicial y alternando los caracteres de las cadenas tomadas)
3. Diseñe autómatas finitos no deterministas para los siguientes lenguajes. Trate de usar epsilon transiciones para simplificar su diseño.
   1. El conjunto de cadenas que consisten en cero o más $a$ seguidas de cero o más $b$ seguidas de cero o más $c$.
   2. El conjunto de cadenas que consisten en 01 repetido una o más veces o 010 repetido una o más veces.
   3. El conjunto de cadenas de 0 y 1 tal que al menos una de las últimas diez posiciones es un 1.
4. Argumente que los siguientes lenguajes son regulares:
   1. Todos los números flotantes.
   2. Todos los números de teléfono cubanos.
   3. Todos los posibles nombres de variables de c#.
   4. Todas las direcciones de correo electrónico.
   5. Todos los posibles comentarios en un lenguaje de programación.
   6. Todos los path de un archivo de linux.

¹ https://es.wikipedia.org/wiki/Estrella_de_Kleene