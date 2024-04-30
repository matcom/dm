# Planaridad

> **Definición:** Un grafo es *planar* si se puede dibujar en un plano sin que se corten las aristas. 

Para ello hay que establecer algunas reglas, que diremos son un dibujo *simple*:
- Los vértices tienen que ocupar posiciones diferentes.
- Cada arista tiene que ser continua, pero no necesariamente recta.
- Ninguna arista se corta a sí misma.
- Dos aristas curvas no se tocan excepto si se cortan.
- Dos aristas se cortan a lo sumo una vez.
- A lo sumo dos aristas se cortan en el mismo punto del plano.

Diremos sin demostración que si tenemos un dibujo de un grafo donde se incumplen algunas de las condiciones anteriores, siempre podemos tener un dibujo con *igual o menos* intersecciones en las aristas, arreglando una de esas condiciones.

> **Definición:** El número de cruzamiento de un grafo $G$, denotado por $\upsilon(G)$ es el menor número de intersecciones entre aristas con que se puede dibujar $G$.

Evidentemente, si $G$ es planar, entonces $\upsilon(G)=0$.

Una forma de dibujar un grafo planar $G$ sin que se corten las aristas se llama un *embedding* de $G$. Evidentemente si existe un embedding de G, existen infinitos, pero no necesariamente infinitos *realmente distintos.*

Dos grafos no planares clásicos son $K_{3,3}$ y $K_{5}$. Luego veremos que son fundamentales.

> **Teorema 12.1 (Fáry):** Si un grafo es planar, se puede dibujar de forma que todas las aristas sean rectas.

No daremos demostración del teorema de Fáry, pero debe verse de forma intuitiva. Sin embargo, sorprendentemente, el número de cruzamiento sí cambia si no permitimos aristas curvas.
## Propiedades de los grafos planares

Un embedding de un grafo genera en el plano un conjunto de **caras**, secciones continuas del plano que no cruzan una arista o vértice. En todo embedding hay una cara externa, y varias caras internas. Los vértices y artistas que delimitan una cara $F$ se denominan la *frontera* de $F$.

> **Teorema 12.2 (Euler):** Sea $G$ un grafo conexo planar con $n=|V|$ y $m=|E|$, entonces en todo embedding de $G$ con $f$ caras se cumple que $n-m+f=2$.

**Idea de demostración:** Inducción en $m$. Si $m=0$, $G \simeq K_1$, por lo que $n=1,f=1$. Si $m>1$ y $G$ es un árbol, entonces $f=1, m=n-1$. Supongamos que $G$ tiene un ciclo, entonces hay una arista $e$ en ese ciclo. Al quitar dicha arista exactamente dos caras se convierten en una. 

Daremos sin demostración otra propiedad interesante que nos servirá luego:

> **Lema 12.3:** En todo grafo planar $G$, para todo vértice $v$, existe un embedding en el cuál $v$ está en la frontera de la cara externa.

Intuitivamente, un grafo planar no puede tener demasiadas aristas. Intentemos cuantificar esta idea. Primero veamos que cada arista en un embedding es frontera de exactamente una o dos caras. Por otro lado, cada cara tiene como mínimo 3 aristas. Con esto podemos demostrar el siguiente teorema.

> **Teorema 12.4:** Si $G$ es planar con orden $n≥3$ entonces tiene tamaño $m \leq 3n-6$.

**Idea de demostración:** Sea $M$ la suma de las aristas en la frontera de cada cara (contando la misma arista todas las veces que aparezca), entonces $M \leq 2m$. Sin embargo, como cada cara tiene 3 aristas o mas, $M \geq 3f$. Por tanto, $3f \leq 2m$, o $f \leq \frac{2m}{3}$. Aplicando Euler, $2 = n-m+f \leq n-m+\frac{2m}{3} = n-\frac{m}{3}$, o $6 \leq 3n-m$.

De aquí nos debe salir intuitivamente, que el grado de los vértices de $G$ tampoco puede ser muy grande, porque tendría demasiadas aristas.

> **Teorema 12.4:** En todo grafo planar $G$ hay al menos un vértice con $d(v) \leq 5$.

**Idea de demostración:** Si todo vértice tiene $d(v) \geq 6$ entonces $\sum d(v) = 2m \geq 6n$ lo que contradice el teorema 12.3.

Con estas ideas podemos demostrar la no-planaridad de los grafos más básicos, $K_{3,3}$ y $K_{5}$ que dejaremos para CP.

## Caracterizando los grafos no planares

Vamos a comenzar viendo que todo grafo que contiene un subgrafo no-planar también es no planar. Por tanto para estudiar la planaridad conviene estudiar casos extremos de grafos no-planares que aparezcan como subgrafos en todos los grafos no-planares. ¿Será esto posible?

Empecemos por ver cómo un subgrafo no planar puede aparecer en un grafo más grande.

Una primera idea intuitiva es que si una arista cualquiera $xy$ la sustituimos por un nuevo vértice $z$ con las aristas $xz$ y $zy$ la planaridad no cambia. Llamaremos a este proceso una **subdivisión**.

> **Definición:** Si un grafo $G$ contiene una subdivisión de un grafo $H$ como subgrafo, entonces decimos que $H$ es un **menor topológico** de $G$.

Evidentemente, si $G$ tiene a $K_{3,3}$ o $K_{5}$ como menor topológico, $G$ es no planar. El resultado más sorprendente de esta conferencia es justamente que el recíproco también es cierto.

> **Teorema 12.5 (Kuratoski):** Un grafo $G$ es planar si y solo si no contiene a $K_{3,3}$ o $K_{5}$ como menor topológico.

La operación contraria a la subdivisión es una contracción. Sin embargo, al contraer podemos eliminar cualquier vértice, no solo un vértice de grado 2. Si hacemos eso, obtenemos lo que se llama un **menor** en el sentido más general. El teorema de Wagner nos da una conexión con Kuratoski interesante:

> **Teorema 12.5 (Wagner):** Un grafo $G$ es planar si y solo si no contiene a $K_{3,3}$ o $K_{5}$ como menor (no necesariamente topológico).

Dado que un menor topológico es un menor en el sentido general, solo sería necesario probar que si un grafo contiene un menor de $K_{3,3}$ o $K_{5}$, debe contener también un menor topológico de alguno de estos (no necesariamente el mismo).

## Coloreando grafos planares

Vamos a concluir con una breve exploración del problema de coloración en grafos planares. La pregunta que queremos responder es si existe alguna cota superior para $\chi(G)$ en grafos planares.

Dado que todo grafo planar $G$ tiene un vértice con $deg(v) \leq 5$ es evidente que $\chi(G) \leq 6$. (¿Por qué?) Pero podemos bajarlo a 5 relativamente fácil.

> **Teorema 12.6 (5 colores):** Todo grafo planar puede ser coloreado con 5 colores.

**Idea de demostración:** Vamos a hacerlo por inducción en $n=|V|$. Evidentemente hasta $n=5$ es fácil. Supongamos que para $n-1$ está demostrado, sea $G$ un grafo planar de orden $n$ y $v$ un vértice con $deg(v) \leq 5$. 
Por hipótesis de inducción, $G-5$ es 5-coloreable, por lo tanto, si $deg(v)<5$o algún par de vecinos de $v$ repite color, es fácil ver que $G$ es 5-coloreable. Asumamos entonces una 5-coloración de $G-v$ donde los 5 vecinos de $v$ tienen colores diferentes, y veamos un embedding de $G$ en el plano, sean $v_{1} \dots v_{5}$ los 5 vecinos de $v$ coloreados respectivamente con los colores $1 \dots 5$, en sentido de las manecillas del reloj.
Veamos ahora el subgrafo $H$ inducido por todos los vértices alcanzables desde $v_1$ que están en caminos coloreados de forma alternada con colores $1$ y $3$ solamente. Pueden pasar dos cosas, o este subgrafo contiene a $v_{3}$ o no. Si $v_{3} \not\in H$ entonces es posible intercambiar todos los colores en ese subgrafo y producir una 5-coloración válida, pero ahora $v_{1}$ y $v_{3}$ tienen el mismo color, luego queda un color disponible para $v$.
Por el contrario, si $v_{3} \in H$, entonces el camino entre $v_{1}$ y $v_{3}$ me tiene que separar a $v_{2}$ de $v_{4}$, por lo tanto no puede haber un camino de $v_{2}$ a $v_{4}$ compuesto solo de colores $2$ y $4$, porque en algún punto hay que pasar por un vértice de $H$. Por lo tanto, hago lo mismo con $v_{2}$ y recoloreo.

¿Se puede bajar de 5 colores? Sorprendentemente, sí.

> **Teorema 12.6 (4 colores):** Todo grafo planar puede ser coloreado con 4 colores.

Sin embargo, la demostración de este teorema es imposible de realizar manualmente. Este es el primer teorema que requirió de un uso intensivo de algoritmos de búsqueda para ser demostrado, en 1976. Muy básicamente, la demostración pasa por encontrar un conjunto de configuraciones reducibles tal que todo grafo planar debe tener algún elemento de ese conjunto. A base de algoritmos de búsqueda y heurísticas, se lograron encontrar un conjunto de 1476 configuraciones, que posteriormente fue mejorado considerablemente.