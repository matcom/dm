# Discreta II

## Clase Practica #2

1. Construya un autómata que reconozca el lenguaje de las cadenas sobre el alfabeto {a, b} que:
   1. Tienen una cantidad par de "a"
   2. Tienen una cantidad par de "a" e impar de "b"
   3. Tienen dos "a" consecutivas en algún lugar de la cadena
   4. Tienen dos "a" consecutivas en algún lugar de la cadena, pero no al final
   
2. Construya un autómata que reconozca el lenguaje L de las cadenas que son el resultado de concatenar un número positivo de veces la cadena "ab"
   1. Construya un autómata que reconozca el lenguaje de las cadenas que son el resultado de concatenar una cadena del lenguaje L y una cadena del lenguaje de todas las posibles cadenas sobre el alfabeto  {a, b}

3. Construya un autómata que reconozca el lenguaje de las cadenas *x2y* donde *x* y *y* son cadenas sobre el alfabeto {0, 1} tal que: 
   1. El número que representa cada una es divisible por 3.
   2. \* La suma de los números representados por las cadenas *x* y *y* es divisible por 3

4. Sea Q el conjunto de todas las listas no vacías de enteros positivos y L el conjunto de todas las cadenas sobre el alfabeto {0, 1}. Se define la función $f: Q \rightarrow L$ tal que:
   
    $f(l) = (1)^{a_1}0(1)^{a_2}0 \ldots 0(1)^{a_k}$ donde $l = \{ a_1, a_2, ..., a_k \} \in Q$

   Por ejemplo, $f(2, 3, 2) = 110111011$.
   
   Construya el autómata que reconoce el lenguaje de las cadenas que pertenecen a la imagen de f.

5. Determine el conjunto de longitudes posibles de las cadenas que reconoce el siguiente automata:

   ![automata](images/automata-cp2-ex4.png)

6. Construya el autómata que reconozca dado un camino, si este representa un ciclo simple en el siguiente grafo:
   
   ![graph](images/graph-cp2-ex5.png)
   
7. Construya el autómata que reconozca el lenguaje de las cadenas sobre el alfabeto {a, b, c} tales que contengan una 'a' en todas las posiciones pares excepto en las que son múltiplo de 3.

8. \* Construya el autómata que reconoce el siguiente lenguaje sobre el alfabeto {0, 1}
   1.  El conjunto de todas las cadenas tal que cada bloque de cinco símbolos consecutivos contenga al menos dos "0"
   2.  El conjunto de todas las cadenas cuyo decimo símbolo desde la derecha es "1"
   3.  El conjunto de todas las cadenas que comienzan o terminan con "01"
   4.  El conjunto de todas las cadenas tal que el número de "0" es divisible por 5 y el número de "1" es divisible por 3

9.  \*\* Construya el autómata que reconoce el siguiente lenguaje sobre el alfabeto {0, 1}:
    1.  El conjunto de todas las cadenas que comienzan con "1", y que al ser interpretadas como número binario, son múltiplo de 5. Por ejemplo, las cadenas "101", "1010" y "1111" pertenecen al lenguaje, mientras que "0", "100" y "111" no.
    2.  El conjunto de todas las cadenas, que interpretadas en reverso como un número binario, son divisibles por 5. Por ejemplo, las cadenas "0", "10011", "1001100", y "0101" pertencen a este lenguaje.